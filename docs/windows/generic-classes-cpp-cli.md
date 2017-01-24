---
title: "泛型类 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类 [C++], 泛型"
  - "数据类型 [C++], 泛型"
  - "泛型类"
  - "泛型类 [C++], 关于泛型类"
  - "泛型 [C++], 声明泛型类"
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
caps.latest.revision: 33
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 泛型类 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用以下语法声明派生类：  
  
## 语法  
  
```  
[attributes]  
generic <class-key type-parameter-identifier(s)>  
[constraint-clauses]  
[accessibility-modifiers] ref class identifier  [modifiers]  
[: base-list]   
{  
   class-body  
} [declarators] [;]  
```  
  
## 备注  
 在上述语法，使用以下术语：  
  
 `attributes`（可选）  
 附加的声明信息。  有关特性和特性类的更多信息，请参见特性。  
  
 *类键*  
 为 `class` 或 `typename`  
  
 *类型参数标识符*,  
 指定类型参数的名称的标识符用逗号分隔的列表。  
  
 *constraint\-clauses*  
 列表 \(没有逗号分隔\) 指定约束的 **位置** 子句为类型参数。  它采用格式。  
  
 `where`  *type\-parameter\-identifier*  `:`  *constraint\-list*  `...`  
  
 *constraint\-list*  
 *类或接口* \[`,` *...*\]  
  
 *可见性修饰符*  
 泛型类的可访问性修饰符。  对于，唯一的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]允许修饰符为 `private`。  对于公共语言运行时，允许修饰符是 `private` 和 `public`。  
  
 *identifier*  
 泛型类，任何有效的 C\+\+ 标识符的名称。  
  
 *可选修饰符。*  
 允许修饰符包括 `sealed` 和 **抽象**。  
  
 *base\-list*  
 逗号包含这个基类以及任何实现的接口的列表，所有单独的。  
  
 *class\-body*  
 类包含成员函数体，其中字段，等等。  
  
 *声明符*  
 此的任何变量的声明类型。  例如： `^`…*标识符*\[`,` \]  
  
 可以声明泛型类这些注释 \(如关键字 **类** 可以使用代替 **typename**\)。  在此示例中， `ItemType`、`KeyType` 和 `ValueType` 都是指定位于点的类型未知类型。  `HashTable<int, int>` 是泛型 `HashTable<KeyType, ValueType>`类型的构造类型。  许多不同的构造类型可以从单一泛型类型构造。  从泛型类生成的构造类型像任何其他 ref 类类型。  
  
```  
// generic_classes_1.cpp  
// compile with: /clr  
using namespace System;  
generic <typename ItemType>  
ref struct Stack {  
   // ItemType may be used as a type here  
   void Add(ItemType item) {}  
};  
  
generic <typename KeyType, typename ValueType>  
ref class HashTable {};  
  
// The keyword class may be used instead of typename:  
generic <class ListItem>  
ref class List {};  
  
int main() {  
   HashTable<int, Decimal>^ g1 = gcnew HashTable<int, Decimal>();  
}  
```  
  
 值类型 \(内置类型 \(如 `int`、`double`或用户定义的值类型和引用类型\) 能用作泛型类型参数。  在泛定义中的语法不完全相同。  语法上，未知类型处理，可以像引用类型。  但是，运行时可以确定，如果实际使用的类型是值类型和替换指向成员的直接访问重写适当的生成代码。  为泛型类型参数使用未装箱的值类型，所以不遇到与装箱相关的性能损失。  在文本中使用的语法中常规应是 **T^** 和 '**\-\>**' 而不是 '**.**'。  如果类型参数属于值类型，则类型参数的任何使用 [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) 的将由运行时正确解释用作值类型的简单的创建。  
  
 还可以使用 [约束](../windows/constraints-on-generic-type-parameters-cpp-cli.md) 可以为类型参数的类型声明的泛型类。。  在下面的示例中使用 `ItemType` 的任何类型必须实现 `IItem` 接口。  尝试使用 `int`，例如，不实现 `IItem`，将导致编译时错误，因为类型参数不满足约束。  
  
```  
// generic_classes_2.cpp  
// compile with: /clr /c  
interface class IItem {};  
generic <class ItemType>  
where ItemType : IItem  
ref class Stack {};  
```  
  
 在同一命名空间的泛型类不能通过只更改数量或类型参数的重载。  但是，如果，每个类在其他命名空间中，它们可以重载。  例如，请考虑下面的两类，`MyClass` 和 `MyClass<ItemType>`，在命名空间 `A` 和 `B`。  两个类在第三 C 命名空间会重载：  
  
```  
// generic_classes_3.cpp  
// compile with: /clr /c  
namespace A {  
   ref class MyClass {};  
}  
  
namespace B {  
   generic <typename ItemType>   
   ref class MyClass2 { };  
}  
  
namespace C {  
   using namespace A;  
   using namespace B;  
  
   ref class Test {  
      static void F() {  
         MyClass^ m1 = gcnew MyClass();   // OK  
         MyClass2<int>^ m2 = gcnew MyClass2<int>();   // OK  
      }  
   };  
}  
```  
  
 基类和\/或基接口不能为类型参数。  但是，基类可以涉及类型参数作为参数，如以下情况：  
  
```  
// generic_classes_4.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
interface class IInterface {};  
  
generic <typename ItemType>  
ref class MyClass : IInterface<ItemType> {};  
```  
  
 构造函数和析构函数。每个对象实例执行一次 \(及平常相同\);静态构造函数的每个构造的类型执行一次。  
  
## 泛型类的字段  
 本节演示如何使用泛型类的实例和静态字段。  
  
### 实例变量  
 泛型类的实例变量可以有包含的任何一种都从封闭类的参数变量的类型和初始值设定项。  
  
## 示例  
 使用适当的类型参数 \(`int`、**双倍行距**和 **字符串**\)，在\<\>下面示例中，泛型类，MyClassItemType 的三种不同实例，创建。  
  
```  
// generics_instance_fields1.cpp  
// compile with: /clr  
// Instance fields on generic classes  
using namespace System;  
  
generic <typename ItemType>  
ref class MyClass {  
// Field of the type ItemType:  
public :  
   ItemType field1;  
   // Constructor using a parameter of the type ItemType:  
   MyClass(ItemType p) {  
     field1 = p;   
   }  
};  
  
int main() {  
   // Instantiate an instance with an integer field:  
   MyClass<int>^ myObj1 = gcnew MyClass<int>(123);  
   Console::WriteLine("Integer field = {0}", myObj1->field1);  
  
   // Instantiate an instance with a double field:  
   MyClass<double>^ myObj2 = gcnew MyClass<double>(1.23);  
   Console::WriteLine("Double field = {0}", myObj2->field1);  
  
   // Instantiate an instance with a String field:  
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>("ABC");  
   Console::WriteLine("String field = {0}", myObj3->field1);  
   }  
```  
  
  **Integer 字段为 123**  
**Double 字段为 1.23**  
**字符串字段 \= ABC**    
## 静态变量。  
 在泛型类型的创建，任何静态变量创建新实例，而该类型的任何静态构造函数执行。  
  
 静态变量中使用封闭的类的类型参数。  
  
## 示例  
 下面的示例演示了的静态字段和静态构造函数。泛型类中。  
  
```  
// generics_static2.cpp  
// compile with: /clr  
using namespace System;  
  
interface class ILog {  
   void Write(String^ s);  
};  
  
ref class DateTimeLog : ILog {  
public:  
   virtual void Write(String^ s) {  
      Console::WriteLine( "{0}\t{1}", DateTime::Now, s);  
   }  
};  
  
ref class PlainLog : ILog {  
public:  
   virtual void Write(String^ s) { Console::WriteLine(s); }  
};  
  
generic <typename LogType>  
where LogType : ILog  
ref class G {  
   static LogType s_log;  
  
public:  
   G(){}  
   void SetLog(LogType log) { s_log = log; }  
   void F() { s_log->Write("Test1"); }  
   static G() { Console::WriteLine("Static constructor called."); }     
};  
  
int main() {  
   G<PlainLog^>^ g1 = gcnew G<PlainLog^>();  
   g1->SetLog(gcnew PlainLog());  
   g1->F();  
  
   G<DateTimeLog^>^ g2 = gcnew G<DateTimeLog^>();  
   g2->SetLog(gcnew DateTimeLog());  
  
   // prints date  
   // g2->F();  
}  
```  
  
  **调用的静态构造函数。**  
**调用的静态构造函数。**  
**调用的静态构造函数。**  
**Test1**   
## 在泛型类的方法  
 常规类的方法可以为泛它们；非泛方法将由类隐式类型参数进行参数化。  
  
 以下特殊规则适用于在泛型类中的方法：  
  
-   常规类的方法可将类型参数作为参数、返回类型或局部变量。  
  
-   常规类的方法可以使用开放式或封闭式构造类型作为参数，返回类型或局部变量。  
  
### 在泛型类的非泛型方法  
 在没有的附加类型参数的泛型类的方法通常称为非泛型，尽管它们由封闭泛型类隐式进行参数化。  
  
 非泛型方法的签名可包含对封闭类的一个或多个类型参数，直接或在打开构造的类型。  例如：  
  
 `void MyMethod(MyClass<ItemType> x) {}`  
  
 此方法主体还可以使用这些类型参数。  
  
## 示例  
 下面的示例声明非泛型 `ProtectData`方法，在该泛型类内部，`MyClass<ItemType>`。  在其方法在打开的构造类型的签名使用类的类型参数 `ItemType`。  
  
```  
// generics_non_generic_methods1.cpp  
// compile with: /clr  
// Non-generic methods within a generic class.  
using namespace System;  
  
generic <typename ItemType>  
ref class MyClass {  
public:  
   String^ name;  
   ItemType data;  
  
   MyClass(ItemType x) {  
      data = x;  
   }  
  
   // Non-generic method using the type parameter:  
   virtual void ProtectData(MyClass<ItemType>^ x) {  
      data = x->data;  
   }  
};  
  
// ItemType defined as String^  
ref class MyMainClass: MyClass<String^> {  
public:  
   // Passing "123.00" to the constructor:  
   MyMainClass(): MyClass<String^>("123.00") {  
      name = "Jeff Smith";   
   }   
  
   virtual void ProtectData(MyClass<String^>^ x) override {  
      x->data = String::Format("${0}**", x->data);  
   }  
  
   static void Main() {  
      MyMainClass^ x1 = gcnew MyMainClass();  
  
      x1->ProtectData(x1);  
      Console::WriteLine("Name: {0}", x1->name);  
      Console::WriteLine("Amount: {0}", x1->data);  
   }  
};  
  
int main() {  
   MyMainClass::Main();  
}  
```  
  
  **Name: Jeff Smith**  
**金额：$123.00\*\***   
## 在泛型类的非泛型方法  
 可以在声明泛型和非泛型类的泛型方法。  例如：  
  
## 示例  
  
```  
// generics_method2.cpp  
// compile with: /clr /c  
generic <typename Type1>  
ref class G {  
public:  
   // Generic method having a type parameter  
   // from the class, Type1, and its own type  
   // parameter, Type2  
   generic <typename Type2>  
   void Method1(Type1 t1, Type2 t2) { F(t1, t2); }  
  
   // Non-generic method:  
   // Can use the class type param, Type1, but not Type2.  
   void Method2(Type1 t1) { F(t1, t1); }  
  
   void F(Object^ o1, Object^ o2) {}  
};  
```  
  
 非泛型方法是泛型，从这个意义上来讲它的类的类型参数进行参数化，但没有附加的类型参数。  
  
 方法的所有类型在泛型类的可以为泛，包括静态和实例，虚方法。  
  
## 示例  
 下面的示例演示声明和使用在泛型类中的泛型方法：  
  
```  
// generics_generic_method2.cpp  
// compile with: /clr  
using namespace System;  
generic <class ItemType>  
ref class MyClass {  
public:  
   // Declare a generic method member.  
   generic <class Type1>  
   String^ MyMethod(ItemType item, Type1 t) {  
      return String::Concat(item->ToString(), t->ToString());  
   }  
};  
  
int main() {  
   // Create instances using different types.  
   MyClass<int>^ myObj1 = gcnew MyClass<int>();  
   MyClass<String^>^ myObj2 = gcnew MyClass<String^>();  
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>();  
  
   // Calling MyMethod using two integers.  
   Console::WriteLine("MyMethod returned: {0}",  
            myObj1->MyMethod<int>(1, 2));  
  
   // Calling MyMethod using an integer and a string.  
   Console::WriteLine("MyMethod returned: {0}",  
            myObj2->MyMethod<int>("Hello #", 1));  
  
   // Calling MyMethod using two strings.  
   Console::WriteLine("MyMethod returned: {0}",  
       myObj3->MyMethod<String^>("Hello ", "World!"));  
  
   // generic methods can be called without specifying type arguments  
   myObj1->MyMethod<int>(1, 2);  
   myObj2->MyMethod<int>("Hello #", 1);  
   myObj3->MyMethod<String^>("Hello ", "World!");  
}  
```  
  
  **MyMethod 返回：12**  
**MyMethod 返回：Hello \#1。**  
**MyMethod 返回：Hello World\!**   
## 使用常规类的嵌套类型  
 就像普通类，可以声明一个泛型类中的其他类型。  嵌套类声明由外部类声明类型参数隐式进行参数化。  因此，不同的嵌套类为每个构造的外部类型定义。  例如，在声明中，  
  
```  
// generic_classes_5.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
ref struct Outer {  
   ref class Inner {};  
};  
```  
  
 类型\<\>Outerint::Inner 与类型\<\>Outerdouble::Inner。  
  
 与泛型类的泛型方法，则其他参数的类型可以对嵌套类型定义。  如果在内部和外部类使用相同类型参数的名称，内部类型参数将隐藏外部类型参数。  
  
```  
// generic_classes_6.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
ref class Outer {  
   ItemType outer_item;   // refers to outer ItemType  
  
   generic <typename ItemType>  
   ref class Inner {  
      ItemType inner_item;   // refers to Inner ItemType  
   };  
};  
```  
  
 在这种情况下因为无法引用外部类型变量，编译器将产生警告。  
  
 当构造的嵌套泛型类型名为时，外部类型的类型参数。内部类型的类型参数列表中不包含，因此，即使一内部类型由外部类型的隐式类型参数进行参数化。  上述情况，构造的类型名称是\<\>Outerint::Innerstring\<\>。  
  
 使用常规类，嵌套类型的以下示例演示生成和读取的链接列表。  
  
## 示例  
  
```  
// generics_linked_list.cpp  
// compile with: /clr  
using namespace System;  
generic <class ItemType>  
ref class LinkedList {  
// The node class:  
public:  
   ref class Node {  
   // The link field:  
   public:  
      Node^ next;  
      // The data field:  
      ItemType item;   
   } ^first, ^current;  
};  
  
ref class ListBuilder {  
public:  
   void BuildIt(LinkedList<double>^ list) {  
      /* Build the list */  
      double m[5] = {0.1, 0.2, 0.3, 0.4, 0.5};  
      Console::WriteLine("Building the list:");  
  
      for (int n=0; n<=4; n++) {  
         // Create a new node:  
         list->current = gcnew LinkedList<double>::Node();  
  
         // Assign a value to the data field:  
         list->current->item = m[n];  
  
         // Set the link field "next" to be the same as   
         // the "first" field:  
         list->current->next = list->first;  
  
         // Redirect "first" to the new node:  
         list->first = list->current;  
  
         // Display node's data as it builds:  
         Console::WriteLine(list->current->item);  
      }  
   }  
  
   void ReadIt(LinkedList<double>^ list) {  
      // Read the list  
      // Make "first" the "current" link field:  
      list->current = list->first;  
      Console::WriteLine("Reading nodes:");  
  
      // Read nodes until current == null:  
      while (list->current != nullptr) {  
         // Display the node's data field:  
         Console::WriteLine(list->current->item);  
  
         // Move to the next node:  
         list->current = list->current->next;  
      }  
   }  
};  
  
int main() {  
   // Create a list:  
   LinkedList<double>^ aList = gcnew LinkedList<double>();  
  
   // Initialize first node:  
   aList->first = nullptr;  
  
   // Instantiate the class, build, and read the list:   
   ListBuilder^ myListBuilder = gcnew ListBuilder();  
   myListBuilder->BuildIt(aList);  
   myListBuilder->ReadIt(aList);  
}  
```  
  
  **生成列表：**  
**0.1**  
**0.2**  
**0.3**  
**0.4**  
**0.5**  
**读取节点：**  
**0.5**  
**0.4**  
**0.3**  
**0.2**  
**0.1**   
## 属性索引器、事件、运算符和泛型类的  
  
-   当 `ItemType` 为类类型的参数时，属性、索引器、事件和运算符使用封闭泛型类的类型参数用作返回值，其中参数或局部变量，例如：  
  
    ```  
    public ItemType MyProperty {}  
    ```  
  
-   属性、索引器、事件和运算符无法被参数化。  
  
## 示例  
 此示例演示一实例的声明在泛型类中。  
  
```  
// generics_generic_properties1.cpp  
// compile with: /clr  
using namespace System;  
  
generic <typename ItemType>  
ref class MyClass {  
private:  
   property ItemType myField;  
  
public:  
   property ItemType MyProperty {  
      ItemType get() {  
         return myField;   
      }  
      void set(ItemType value) {  
         myField = value;  
      }  
   }  
};  
  
int main() {  
   MyClass<String^>^ c = gcnew MyClass<String^>();  
   MyClass<int>^ c1 = gcnew MyClass<int>();  
  
   c->MyProperty = "John";  
   c1->MyProperty = 234;  
  
   Console::Write("{0}, {1}", c->MyProperty, c1->MyProperty);  
}  
```  
  
  **John，234**   
## 示例  
 下一个示例演示该事件关联的泛型类。  
  
```  
// generics_generic_with_event.cpp  
// compile with: /clr  
// Declare a generic class with an event and  
// invoke events.  
using namespace System;  
  
// declare delegates  
generic <typename ItemType>  
delegate void ClickEventHandler(ItemType);  
  
// generic class that defines events  
generic <typename ItemType>  
ref class EventSource {  
public:  
   // declare the event OnClick  
   event ClickEventHandler<ItemType>^ OnClick;   
   void FireEvents(ItemType item) {  
      // raises events  
      OnClick(item);  
   }  
};  
  
// generic class that defines methods that will called when  
// event occurs  
generic <typename ItemType>  
ref class EventReceiver {  
public:  
   void OnMyClick(ItemType item) {  
     Console::WriteLine("OnClick: {0}", item);  
   }  
};  
  
int main() {  
   EventSource<String^>^ MyEventSourceString =  
                   gcnew EventSource<String^>();  
   EventSource<int>^ MyEventSourceInt = gcnew EventSource<int>();  
   EventReceiver<String^>^ MyEventReceiverString =  
                   gcnew EventReceiver<String^>();  
   EventReceiver<int>^ MyEventReceiverInt = gcnew EventReceiver<int>();  
  
   // hook handler to event  
   MyEventSourceString->OnClick += gcnew ClickEventHandler<String^>(  
       MyEventReceiverString, &EventReceiver<String^>::OnMyClick);  
   MyEventSourceInt->OnClick += gcnew ClickEventHandler<int>(  
             MyEventReceiverInt, &EventReceiver<int>::OnMyClick);  
  
   // invoke events  
   MyEventSourceString->FireEvents("Hello");  
   MyEventSourceInt->FireEvents(112);  
  
   // unhook handler to event  
   MyEventSourceString->OnClick -= gcnew ClickEventHandler<String^>(  
        MyEventReceiverString, &EventReceiver<String^>::OnMyClick);  
   MyEventSourceInt->OnClick -= gcnew ClickEventHandler<int>(  
        MyEventReceiverInt, &EventReceiver<int>::OnMyClick);  
}  
```  
  
## 泛型结构  
 规则用于声明和使用泛型结构与某些泛型类的，只是在 Visual C\+\+ 语言参考注意的差异。  
  
## 示例  
 下面的示例声明一泛型结构，`MyGenStruct`，因此具有字段，`myField`，并将值赋予不同的类型 \(`int`、**双倍行距**，**String^**\) 到此字段。  
  
```  
// generics_generic_struct1.cpp  
// compile with: /clr  
using namespace System;  
  
generic <typename ItemType>  
ref struct MyGenStruct {  
public:  
   ItemType myField;  
  
   ItemType AssignValue(ItemType item) {  
      myField = item;  
      return myField;  
   }  
};  
  
int main() {  
   int myInt = 123;  
   MyGenStruct<int>^ myIntObj = gcnew MyGenStruct<int>();  
   myIntObj->AssignValue(myInt);  
   Console::WriteLine("The field is assigned the integer value: {0}",  
            myIntObj->myField);  
  
   double myDouble = 0.123;  
   MyGenStruct<double>^ myDoubleObj = gcnew MyGenStruct<double>();  
   myDoubleObj->AssignValue(myDouble);  
   Console::WriteLine("The field is assigned the double value: {0}",  
            myDoubleObj->myField);  
  
   String^ myString = "Hello Generics!";  
   MyGenStruct<String^>^ myStringObj = gcnew MyGenStruct<String^>();  
   myStringObj->AssignValue(myString);  
   Console::WriteLine("The field is assigned the string: {0}",  
            myStringObj->myField);  
}  
```  
  
  **将此值分配给整数变量123 。**  
**字段将双精度值：0.123**  
**字段分配字符串：Hello\!泛型**   
## 请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)