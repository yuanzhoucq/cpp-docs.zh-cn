---
title: CLR 引用类对象的声明 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- types [C++], reference types
- reference types, CLR
ms.assetid: 6d64f746-3715-4948-ada3-88859f4150e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f3e8ec6407e12d0c26331d45dc1659277feed016
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444575"
---
# <a name="declaration-of-a-clr-reference-class-object"></a>CLR 引用类对象的声明

语法来声明和实例化一个引用类类型的对象已从托管扩展中的 c + + 更改为 Visual c + +。

在托管扩展中，通过使用可选的请使用 ISO c + + 指针语法，声明引用类类型对象`__gc`星型左侧的关键字 (`*`)。 例如，以下是各种引用类类型对象的托管扩展语法声明：

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

通过使用新的声明性标记下的新语法声明引用类类型对象 (`^`) 称为正式*跟踪句柄*以及更通俗地说*hat*。 （跟踪形容词意味着引用类型位于 CLR 堆，因此在垃圾回收堆压缩期间可以透明地移动位置。 在运行时以透明方式更新跟踪句柄。 两个类似的概念*跟踪引用*(`%`)，和*内部指针*(`interior_ptr<>`) 中讨论了[值类型语义](../dotnet/value-type-semantics.md)。

若要移动的 ISO c + + 指针语法在重用的声明性语法的主要原因是，如下所示：

- 使用指针语法不允许重载的运算符直接应用于引用对象。 而是一个必须使用其内部名称，如调用运算符`rV1->op_Addition(rV2)`而不是更直观`rV1+rV2`。

- 大量的指针操作，例如强制转换和指针算法，不允许的对象存储在垃圾回收堆中。 这一概念的更好地跟踪句柄捕获 CLR 引用类型的特性。

`__gc`跟踪句柄上的修饰符，没有必要也不受支持。 使用对象本身不会更改;它仍然可以通过指针成员选择运算符访问成员 (`->`)。 例如，下面是前面的托管扩展代码示例转换为新的语法：

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

## <a name="dynamic-allocation-of-an-object-on-the-clr-heap"></a>在 CLR 堆上对象的动态分配

在托管扩展中，存在两个`new`表达式要在本机和托管堆之间分配了很大程度上透明。 在几乎所有情况下，编译器就能够使用上下文来确定是否从本机或托管堆分配内存。 例如，应用于对象的

```
Button *button1 = new Button; // OK: managed heap
int *pi1 = new int;           // OK: native heap
Int32 *pi2 = new Int32;       // OK: managed heap
```

如果不想上下文的堆分配，无法直接使用编译器`__gc`或`__nogc`关键字。 在新语法中，两个新表达式的各自的特性变为显式引入`gcnew`关键字。 例如，以前的三个声明中的新语法如下所示：

```
Button^ button1 = gcnew Button;        // OK: managed heap
int * pi1 = new int;                   // OK: native heap
Int32^ pi2 = gcnew Int32; // OK: managed heap
```

下面是托管扩展初始化`Form1`上一节中声明的成员：

```
void InitializeComponent() {
   components = new System::ComponentModel::Container();
   button1 = new System::Windows::Forms::Button();
   myDataGrid = new DataGrid();

   button1->Click +=
      new System::EventHandler(this, &Form1::button1_Click);
}
```

下面是将转换为新的语法的同一个初始化。 请注意，hat 不需要，对于引用类型时的目标`gcnew`表达式。

```
void InitializeComponent() {
   components = gcnew System::ComponentModel::Container;
   button1 = gcnew System::Windows::Forms::Button;
   myDataGrid = gcnew DataGrid;

   button1->Click +=
      gcnew System::EventHandler( this, &Form1::button1_Click );
}
```

## <a name="a-tracking-reference-to-no-object"></a>对没有对象的跟踪引用

在新语法中，`0`不再表示 null 地址而被视为一个整数，与相同`1`， `10`，或`100`。 新的特殊标记表示的跟踪引用的 null 值。 例如，在托管扩展中，我们初始化引用类型来不寻址任何对象，如下所示：

```
// OK: we set obj to refer to no object
Object * obj = 0;

// Error: no implicit boxing
Object * obj2 = 1;
```

在新语法中，任何初始化或赋值值的类型为`Object`导致该值类型的隐式装箱。 在新语法中，同时`obj`和`obj2`都初始化为寻址装箱的 Int32 对象分别包含值 0 和 1。 例如：

```
// causes the implicit boxing of both 0 and 1
Object ^ obj = 0;
Object ^ obj2 = 1;
```

因此，若要执行显式初始化、 分配和跟踪句柄为 null 的比较，使用新的关键字`nullptr`。  正确版本的原始示例如下所示：

```
// OK: we set obj to refer to no object
Object ^ obj = nullptr;

// OK: we initialize obj2 to a Int32^
Object ^ obj2 = 1;
```

这会增加复杂性某种程度上将现有代码移植到新的语法。 例如，考虑以下值类声明：

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

在这里，同时`args`和`env`是 CLR 引用类型。 为这两个成员的初始化`0`的构造函数中不能保持正在转换到新的语法不变。 相反，它们必须将更改为`nullptr`:

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

同样，对于这些成员进行比较到测试`0`也必须更改要比较为成员`nullptr`。 下面是托管扩展语法：

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

下面是修订版本，替换每个`0`实例与`nullptr`。 通过自动执行许多，翻译工具可帮助在此转换，如果不是所有匹配项，包括使用的`NULL`宏。

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

`nullptr`转换为任何指针或跟踪句柄类型，但不是提升为一种整型类型。 例如，在初始化，下面的一组`nullptr`仅作为对前两个初始值有效。

```
// OK: we set obj and pstr to refer to no object
Object^ obj = nullptr;
char*   pstr = nullptr; // 0 would also work here

// Error: no conversion of nullptr to 0
int ival = nullptr;
```

同样，给定一组重载的方法如下所示：

```
void f( Object^ ); // (1)
void f( char* );   // (2)
void f( int );     // (3)
```

通过调用`nullptr`文本，如下所示，

```
// Error: ambiguous: matches (1) and (2)
f(  nullptr );
```

不明确，因为`nullptr`匹配跟踪句柄和一个指针，并且没有授予而不是另一种类型没有首选项。 （这种情况下需要显式强制转换来消除歧义。）

通过调用`0`完全匹配项实例 (3):

```
// OK: matches (3)
f( 0 );
```

因为`0`是整数类型。 已`f(int)`不存在，请调用将明确地匹配`f(char*)`通过标准转换。 匹配规则使完全匹配项的优先级高于标准转换。 如果没有完全匹配，标准转换是优先于值类型的隐式装箱。 这是原因没有歧义。

## <a name="see-also"></a>请参阅

[将托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[对象句柄运算符 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)<br/>
[nullptr](../windows/nullptr-cpp-component-extensions.md)