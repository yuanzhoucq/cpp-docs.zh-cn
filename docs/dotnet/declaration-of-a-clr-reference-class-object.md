---
title: "CLR 引用类对象的声明 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "引用类型, CLR"
  - "类型 [C++], 引用类型"
ms.assetid: 6d64f746-3715-4948-ada3-88859f4150e4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLR 引用类对象的声明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，声明和实例化引用类类型的对象的语法已发生更改。  
  
 在托管扩展中，通过使用 ISO\-C\+\+ 指针语法，选择在星型 \(`*`\) 的左侧使用 `__gc` 关键字，可声明引用类类型对象。  例如，下面是使用托管扩展语法的各种引用类类型对象声明：  
  
```  
public __gc class Form1 : public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container __gc *components;  
   Button __gc *button1;  
   DataGrid __gc *myDataGrid;     
   DataSet __gc *myDataSet;  
  
   void PrintValues( Array* myArr ) {  
      System::Collections::IEnumerator* myEnumerator =   
         myArr->GetEnumerator();  
  
      Array *localArray;  
      myArr->Copy(myArr, localArray, myArr->Length);  
   }  
};  
```  
  
 在新语法下，引用类类型对象是使用新的声明标记 \(`^`\) 声明的，该标记正式名称为“跟踪句柄”，非正式名称为“帽子符”。（“跟踪”这一形容词表示引用类型位于 CLR 堆内，因此在垃圾回收堆压缩期间可透明地移动位置。）  跟踪句柄在运行时透明地更新。  [值类型语义](../dotnet/value-type-semantics.md) 中讨论了两个类似的概念：“跟踪引用”\(`%`\) 和“内部指针”\(`interior_ptr<>`\)。  
  
 在重用 ISO\-C\+\+ 指针语法中取消声明语法的主要原因如下：  
  
-   使用指针语法后，将不允许重载运算符直接应用于引用对象。  人们不得不使用运算符的内部名称（如 `rV1->op_Addition(rV2)`）而不能使用更为直观的 `rV1+rV2` 来调用运算符。  
  
-   对于在垃圾回收的堆上存储的对象，不允许使用诸如强制转换和指针算法等多个指针操作。  跟踪句柄的概念更好地表现了 CLR 引用类型的本质。  
  
 对于跟踪句柄，没有必要也不支持使用 `__gc` 修饰符。  对象本身的使用未更改；它仍通过指针成员选择运算符 \(`->`\) 来访问成员。  例如，下面是转为使用新语法的上述托管扩展代码示例：  
  
```  
public ref class Form1: public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container^ components;  
   Button^ button1;  
   DataGrid^ myDataGrid;  
   DataSet^ myDataSet;  
  
   void PrintValues( Array^ myArr ) {  
      System::Collections::IEnumerator^ myEnumerator =  
         myArr->GetEnumerator();  
  
      Array ^localArray;  
      myArr->Copy(myArr, localArray, myArr->Length);   }  
};  
```  
  
## CLR 堆上对象的动态分配  
 在托管扩展中，存在要在本机堆和托管堆之间分配的两个 `new` 表达式，这种存在很大程度上是透明的。  在几乎所有实例中，编译器均可使用上下文来确定是否从本机或托管堆分配内存。  例如，  
  
```  
Button *button1 = new Button; // OK: managed heap  
int *pi1 = new int;           // OK: native heap  
Int32 *pi2 = new Int32;       // OK: managed heap  
```  
  
 如果您不想进行上下文堆分配，则可使用 `__gc` 或 `__nogc` 关键字为编译器提供指导。  在新语法中，`gcnew` 关键字的引入使这两个 new 表达式各自的特性变为显式的。  例如，上述三个声明在新语法中如下所示：  
  
```  
Button^ button1 = gcnew Button;        // OK: managed heap  
int * pi1 = new int;                   // OK: native heap  
Int32^ pi2 = gcnew Int32; // OK: managed heap  
```  
  
 下面是在前面的部分中声明的 `Form1` 成员的托管扩展初始化：  
  
```  
void InitializeComponent() {  
   components = new System::ComponentModel::Container();  
   button1 = new System::Windows::Forms::Button();  
   myDataGrid = new DataGrid();  
  
   button1->Click +=   
      new System::EventHandler(this, &Form1::button1_Click);  
}  
```  
  
 下面是重新强制转换为新语法的相同的初始化。  请注意，当引用类型是 `gcnew` 表达式的目标时，不需要帽子。  
  
```  
void InitializeComponent() {  
   components = gcnew System::ComponentModel::Container;  
   button1 = gcnew System::Windows::Forms::Button;  
   myDataGrid = gcnew DataGrid;  
  
   button1->Click +=   
      gcnew System::EventHandler( this, &Form1::button1_Click );  
}  
```  
  
## 对不存在的对象的跟踪引用  
 在新语法中，`0` 不再代表 null 地址，而被视为一个整型数据，`1`、`10` 或 `100` 也是如此。  新的特殊标记代表用来跟踪引用的 null 值。  例如，在托管扩展中，我们初始化一个引用类型来寻址 null 对象，如下所示：  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 在新语法中，值类型到 `Object` 的任何初始化或分配将导致该值类型的隐式装箱。  在新语法中，`obj` 和 `obj2` 都初始化为寻址的、装箱的 Int32 对象，它们分别包含值 0 和 1。  例如：  
  
```  
// causes the implicit boxing of both 0 and 1  
Object ^ obj = 0;  
Object ^ obj2 = 1;  
```  
  
 因此，为了执行显式初始化、分配以及将跟踪句柄与 null 进行比较，请使用新的关键字 `nullptr`。原始示例的正确修订如下所示：  
  
```  
// OK: we set obj to refer to no object  
Object ^ obj = nullptr;  
  
// OK: we initialize obj2 to a Int32^  
Object ^ obj2 = 1;  
```  
  
 这在一定程度上增加了将现有代码移植到新语法中的复杂性。  例如，请考虑以下值类声明：  
  
```  
__value struct Holder {  
   Holder( Continuation* c, Sexpr* v ) {  
      cont = c;  
      value = v;  
      args = 0;  
      env = 0;  
   }  
  
private:  
   Continuation* cont;  
   Sexpr * value;  
   Environment* env;  
   Sexpr * args __gc [];  
};  
```  
  
 这里 `args` 和 `env` 都是 CLR 引用类型。  在转换为新语法时，构造函数中这两个成员到 `0` 的初始化无法保持不变。  相反，它们必须更改为 `nullptr`：  
  
```  
value struct Holder {  
   Holder( Continuation^ c, Sexpr^ v )  
   {  
      cont = c;  
      value = v;  
      args = nullptr;  
      env = nullptr;  
   }  
  
private:  
   Continuation^ cont;  
   Sexpr^ value;  
   Environment^ env;  
   array<Sexpr^>^ args;  
};  
```  
  
 同样，对于将这些成员与 `0` 进行比较的测试，也必须更改为将成员与 `nullptr` 进行比较。  下面是托管扩展语法：  
  
```  
Sexpr * Loop (Sexpr* input) {  
   value = 0;  
   Holder holder = Interpret(this, input, env);  
  
   while (holder.cont != 0) {  
      if (holder.env != 0) {  
         holder=Interpret(holder.cont,holder.value,holder.env);  
      }  
      else if (holder.args != 0) {  
         holder =   
         holder.value->closure()->  
         apply(holder.cont,holder.args);  
      }  
   }  
  
   return value;  
}  
```  
  
 这是修订后的结果，将所有 `0` 实例都替换为了 `nullptr`。  转换工具对此转换帮助很大，它几乎自动转换了所有匹配项，包括 `NULL` 宏的使用。  
  
```  
Sexpr ^ Loop (Sexpr^ input) {  
   value = nullptr;  
   Holder holder = Interpret(this, input, env);  
  
   while ( holder.cont != nullptr ) {  
      if ( holder.env != nullptr ) {  
         holder=Interpret(holder.cont,holder.value,holder.env);  
      }  
      else if (holder.args != nullptr ) {  
         holder =   
         holder.value->closure()->  
         apply(holder.cont,holder.args);  
      }  
   }  
  
   return value;  
}  
```  
  
 `nullptr` 转换为任何指针或跟踪句柄类型，但不提升到整型。  例如，在下列一组初始化中，`nullptr` 只在作为开头两行的初始值时才是有效的。  
  
```  
// OK: we set obj and pstr to refer to no object  
Object^ obj = nullptr;  
char*   pstr = nullptr; // 0 would also work here  
  
// Error: no conversion of nullptr to 0 …  
int ival = nullptr;  
```  
  
 同样给定一组重载方法，如下所示：  
  
```  
void f( Object^ ); // (1)  
void f( char* );   // (2)  
void f( int );     // (3)  
```  
  
 使用 `nullptr` 文本的调用，如下所示，  
  
```  
// Error: ambiguous: matches (1) and (2)  
f(  nullptr );  
```  
  
 是不明确的，因为 `nullptr` 与跟踪句柄和指针都匹配，并且没有指定两个项中的首选项。（这种情况下，需要显式强制转换来消除歧义。）  
  
 使用 `0` 的调用与实例 \(3\) 完全匹配：  
  
```  
// OK: matches (3)  
f( 0 );  
```  
  
 因为 `0` 属于 integer 类型。  假设 `f(int)` 不存在，该调用将通过标准转换与 `f(char*)` 明确地匹配。  匹配规则指定精确匹配优先于标准转换。  没有精确匹配时，值类型的标准转换优先于隐式装箱。  这就是不存在多义性的原因。  
  
## 请参阅  
 [托管类型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)   
 [对象句柄运算符 \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)