---
title: 泛型类 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: deeb40e54c0324874d9c99a42a98e7e852394dc4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643184"
---
# <a name="generic-classes-ccli"></a>泛型类 (C++/CLI)
使用以下形式声明的泛型类：  
  
## <a name="syntax"></a>语法  
  
```cpp  
[attributes]  
generic <class-key type-parameter-identifier(s)>  
[constraint-clauses]  
[accessibility-modifiers] ref class identifier  [modifiers]  
[: base-list]   
{  
class-body  
} [declarators] [;]  
```  
  
## <a name="remarks"></a>备注  
 在上述语法中，使用以下术语：  
  
 *属性*（可选）  
 附加的声明信息。 有关特性和特性类的详细信息，请参阅“特性”。  
  
 *类键*  
 任一**类**或**typename**  
  
 *类型的参数的标识符*，  
 指定的类型参数的名称标识符的逗号分隔列表。  
  
 *约束子句*  
 （不以逗号分隔） 的列表**其中**子句指定的类型参数约束。 采用格式：  
  
 `where`  *类型参数标识符*`:`*约束列表*  `...`  
  
 *约束列表*  
 *类或接口*[`,` *...*]  
  
 *可访问性修饰符*  
 泛型类的可访问性修饰符。 对于 Windows 运行时，是唯一允许的修饰符**专用**。 公共语言运行时，将允许的修饰符**私有**并**公共**。  
  
 *identifier*  
 泛型类，任何有效的 c + + 标识符的名称。  
  
 *修饰符*（可选）  
 允许的修饰符包括**密封**并**抽象**。  
  
 *基础列表*  
 一个列表，其中包含一个基本类和任何实现的接口，所有逗号分隔。  
  
 *类-正文*  
 包含字段、 成员函数等的类的正文。  
  
 *声明符*  
 此类型的任何变量的声明。 例如： `^`*标识符*[`,` ...]  
  
 您可以声明如这些泛型类 (请注意，关键字**类**可能使用而不是**typename**)。 在此示例中， `ItemType`，`KeyType`和`ValueType`指定点处的未知类型的类型。 `HashTable<int, int>` 为泛型类型构造的类型`HashTable<KeyType, ValueType>`。 可以从单一的泛型类型构造的不同构造类型数。 构造泛型类的构造的类型来处理任何其他 ref 类类型。  
  
```cpp  
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
  
 这两值类型 (任一内置类型，如**int**或**double**，或用户定义的值类型) 和引用类型可能用作泛型类型参数。 在泛型定义中的语法是相同的而不考虑。 在语法上，就像引用类型处理未知的类型。 但是，运行时能够确定，如果实际使用的类型是值类型，并使用替代相应生成的代码直接访问成员。 使用作为泛型类型参数的值类型未装箱，并因此不会遇到与装箱的性能损失。 泛型在正文中使用的语法应`T^`并`->`而不是`.`。 任何使用的变量[ref new、 gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)类型参数将被相应地解释由运行时为值类型的简单创建如果类型参数是值类型。  
  
 此外可以声明的泛型类[泛型类型参数的约束 (C + + CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)上可用于类型参数的类型。 在下面的示例使用的任何类型`ItemType`必须实现`IItem`接口。 尝试使用**int**，例如，这不实现`IItem`，会生成编译时错误，因为类型实参不满足该约束。  
  
```cpp  
// generic_classes_2.cpp  
// compile with: /clr /c  
interface class IItem {};  
generic <class ItemType>  
where ItemType : IItem  
ref class Stack {};  
```  
  
 不能通过仅更改数量或类型的类型参数重载相同的命名空间中的泛型类。 但是，如果每个类驻留在不同的命名空间，它们可以进行重载。 例如，考虑以下两个类，`MyClass`并`MyClass<ItemType>`，在命名空间`A`和`B`。 然后可以进行两个类重载在第三个命名空间 c:  
  
```cpp  
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
  
 基类和基接口不能为类型参数。 但是，基类可能涉及类型参数作为参数，如以下用例中所示：  
  
```cpp  
// generic_classes_4.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
interface class IInterface {};  
  
generic <typename ItemType>  
ref class MyClass : IInterface<ItemType> {};  
```  
  
 构造函数和析构函数执行一次为每个对象实例 （像往常一样）;静态构造函数是为每个构造类型执行一次。  
  
## <a name="fields-in-generic-classes"></a>泛型类中的字段  
 本部分演示如何使用的实例和泛型类中的静态字段。  
  
### <a name="instance-variables"></a>实例变量  
 泛型类的实例变量可以具有类型和变量的初始值设定项，其中包括从封闭类的任何类型参数。  
  
## <a name="example"></a>示例  
 在下面的示例中，三个不同实例的泛型类 MyClass\<ItemType >，使用适当的类型参数创建的 (**int**， **double**，和**字符串**)。  
  
```cpp  
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
  
```Output  
Integer field = 123  
Double field = 1.23  
String field = ABC  
```  
  
## <a name="static-variables"></a>静态变量  
 新的泛型类型创建，创建的所有静态变量的新实例并执行该类型的任何静态构造函数。  
  
 静态变量可以使用封闭类中的任何类型参数。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用静态字段和在泛型类的静态构造函数。  
  
```cpp  
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
  
```Output  
Static constructor called.  
Static constructor called.  
Static constructor called.  
Test1  
```  
  
## <a name="methods-in-generic-classes"></a>泛型类中的方法  
 泛型类中的方法可以是泛型本身;非泛型方法将进行隐式参数化的类类型参数。  
  
 以下特殊规则适用于泛型类中的方法：  
  
-   泛型类中的方法可用作参数、 返回类型或本地变量的类型参数。  
  
-   泛型类中的方法可以使用开放或封闭构造的类型作为参数、 返回类型或本地变量。  
  
### <a name="non-generic-methods-in-generic-classes"></a>泛型类中的非泛型方法  
 中没有其他类型参数的泛型类的方法通常称为非泛型尽管它们隐式参数化的封闭泛型类。  
  
 直接或开放式构造类型中，非泛型方法的签名可以包含封闭类的一个或多个类型参数。 例如：  
  
 `void MyMethod(MyClass<ItemType> x) {}`  
  
 此类方法的正文还可以使用这些类型参数。  
  
## <a name="example"></a>示例  
 下面的示例声明一个非泛型方法， `ProtectData`，在泛型类`MyClass<ItemType>`。 该方法使用类类型参数`ItemType`开放式构造类型中的签名中。  
  
```cpp  
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
  
```Output  
Name: Jeff Smith  
Amount: $123.00**  
```  
  
## <a name="generic-methods-in-generic-classes"></a>泛型类中的泛型方法  
 您可以声明泛型和非泛型类中的泛型方法。 例如：  
  
## <a name="example"></a>示例  
  
```cpp  
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
  
 非泛型方法仍为泛型意义上说，它参数化的类的类型参数，但它没有任何其他类型参数。  
  
 所有类型的泛型类中的方法可以都是泛型，其中包括静态、 实例和虚拟方法。  
  
## <a name="example"></a>示例  
 下面的示例演示如何声明和使用泛型类中的泛型方法：  
  
```cpp  
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
  
```Output  
MyMethod returned: 12  
MyMethod returned: Hello #1  
MyMethod returned: Hello World!  
```  
  
## <a name="using-nested-types-in-generic-classes"></a>在泛型类中使用嵌套的类型  
 就像使用普通类，可以声明泛型类中的其他类型。 嵌套的类声明隐式参数化由外部类声明的类型参数。 因此，为每个构造的外部类型定义不同的嵌套的类。 例如，在声明中，  
  
```cpp  
// generic_classes_5.cpp  
// compile with: /clr /c  
generic <typename ItemType>  
ref struct Outer {  
   ref class Inner {};  
};  
```  
  
 类型`Outer<int>::Inner`不是类型相同`Outer<double>::Inner`。  
  
 与泛型类中的泛型方法，可以为嵌套类型定义其他类型参数。 如果在内部和外部类中使用相同的类型参数名称，内部类型参数将隐藏外部类型参数。  
  
```cpp  
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
  
 因为没有方法来引用外部类型参数，编译器会生成警告在此情况下。  
  
 当构造嵌套的泛型类型的命名时，外部类型的类型参数即使内部类型隐式参数化外部类型的类型参数不包含内部类型的类型参数列表中。 在上述情况下，构造类型的名称会`Outer<int>::Inner<string>`。  
  
 下面的示例演示如何生成和读取泛型类中使用嵌套的类型的链接的列表。  
  
## <a name="example"></a>示例  
  
```cpp  
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
  
```Output  
Building the list:  
0.1  
0.2  
0.3  
0.4  
0.5  
Reading nodes:  
0.5  
0.4  
0.3  
0.2  
0.1  
```  
  
## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>属性、 事件、 索引器和泛型类中的运算符  
  
-   属性、 事件、 索引和运算符可以作为返回值、 参数或局部变量，例如何时使用封闭泛型类的类型参数`ItemType`是类的一个类型参数：  
  
    ```cpp  
    public ItemType MyProperty {}  
    ```  
  
-   属性、 事件、 索引和运算符不能对本身参数化。  
  
## <a name="example"></a>示例  
 此示例演示一个在泛型类的实例属性的声明。  
  
```cpp  
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
  
```Output  
John, 234  
```  
  
## <a name="example"></a>示例  
 下面的示例演示事件的泛型类。  
  
```cpp  
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
  
## <a name="generic-structs"></a>泛型结构  
 声明和使用泛型结构的规则是不同于泛型类，但在 Visual c + + 语言参考中所述的差异除外。  
  
## <a name="example"></a>示例  
 下面的示例声明为泛型结构`MyGenStruct`，具有一个字段`myField`，并将分配不同类型的值 (**int**， **double**， `String^`) 对此字段。  
  
```cpp  
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
  
```Output  
The field is assigned the integer value: 123  
The field is assigned the double value: 0.123  
The field is assigned the string: Hello Generics!  
```  
  
## <a name="see-also"></a>请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)