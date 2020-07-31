---
title: 泛型类 (C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
ms.openlocfilehash: 894bbffcc73693e5d0976831d65df54b09c853d2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216019"
---
# <a name="generic-classes-ccli"></a>泛型类 (C++/CLI)

泛型类采用以下声明形式：

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

上面的语法使用了以下术语：

*attributes*<br/>
（可选）其他声明性信息。 有关特性和特性类的详细信息，请参阅“特性”。

class-key**<br/>
**`class`** 或**`typename`**

type-parameter-identifier(s)**：标识符的逗号分隔列表，用于指定类型参数的名称。

constraint-clauses**<br/>
where**** 子句的非逗号分隔列表，用于指定类型参数的约束。 采用以下形式：

> **where** *类型参数标识符* **：** *constraint-list*  **...**

constraint-list**<br/>
*类或接口*[ `,` *...*]

accessibility-modifiers**<br/>
泛型类的可访问性修饰符。 对于 Windows 运行时，唯一允许的修饰符是 **`private`** 。 对于公共语言运行时，允许的修饰符为 **`private`** 和 **`public`** 。

*identifier*<br/>
泛型类的名称，即任意有效的 C++ 标识符。

*组成*<br/>
（可选）允许的修饰符包括 sealed**** 和 abstract****。

base-list**<br/>
包含一个基类和任何实现接口（全都以逗号分隔）的列表。

class-body**<br/>
包含字段、成员函数等的类主体。

*声明符*<br/>
采用此类型的任何变量的声明。 例如： `^` *identifier*[ `,` ...]

可以声明这样的泛型类（请注意，可以使用关键字 **`class`** 而不是 **`typename`** ）。 在此示例中，`ItemType`、`KeyType` 和 `ValueType` 是在类型所在位置指定的未知类型。 `HashTable<int, int>` 是泛型类型 `HashTable<KeyType, ValueType>` 的构造类型。 可以通过一个泛型类型来构造许多不同的构造类型。 将通过泛型类构造的构造类型视为与其他任何 ref class 类型一样。

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

这两个值类型（内置类型（如 **`int`** 或） **`double`** 或用户定义的值类型）和引用类型都可用作泛型类型参数。 无论如何，泛型定义中的语法是相同的。 从语法上讲，将未知类型视为引用类型。 不过，运行时可以确定实际使用的类型是否是值类型，并替换生成的相应代码，以直接访问成员。 用作泛型类型参数的值类型未装箱，因此不会有装箱造成的性能损失。 泛型主体中使用的语法应为 `T^` 和 `->`，而不是 `.`。 运行时会将对类型参数使用 [ref new、gcnew](ref-new-gcnew-cpp-component-extensions.md) 相应地解释为，如果类型参数为值类型，就直接创建值类型。

还可以根据[泛型类型参数的约束 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)，对可用于类型参数的类型声明泛型类。 在下面的示例中，任何用于 `ItemType` 的类型都必须实现 `IItem` 接口。 例如，如果尝试使用不实现的， **`int`** `IItem` 将产生编译时错误，因为类型参数不满足约束。

```cpp
// generic_classes_2.cpp
// compile with: /clr /c
interface class IItem {};
generic <class ItemType>
where ItemType : IItem
ref class Stack {};
```

无法仅通过更改类型参数的数量或类型来重载相同命名空间中的泛型类。 不过，如果每个类位于不同的命名空间中，可以重载它们。 例如，假设以下两个类位于命名空间 `A` 和 `B` 中：`MyClass` 和 `MyClass<ItemType>`。 然后，可以在第三个命名空间 C 中重载这两个类：

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

基类和基接口不得是类型参数。 不过，基类可以将类型参数用作参数，如下面的示例所示：

```cpp
// generic_classes_4.cpp
// compile with: /clr /c
generic <typename ItemType>
interface class IInterface {};

generic <typename ItemType>
ref class MyClass : IInterface<ItemType> {};
```

构造函数和析构函数对每个对象实例执行一次（照常）；静态构造函数对每个构造类型执行一次。

## <a name="fields-in-generic-classes"></a>泛型类中的字段

此部分展示了如何在泛型类中使用实例字段和静态字段。

### <a name="instance-variables"></a>实例变量

泛型类的实例变量可以有类型和变量初始值设定项，其中包括封闭类中的任何类型参数。

## <a name="example"></a>示例

在下面的示例中， \<ItemType> 通过使用相应的类型自变量（ **`int`** 、 **`double`** 和**字符串**）创建泛型类 MyClass 的三个不同实例。

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

新建泛型类型后，便会创建任何静态变量的新实例，并执行相应类型的任何静态构造函数。

静态变量可以使用封闭类中的任何类型参数。

## <a name="example"></a>示例

下面的示例展示了如何在泛型类中使用静态字段和静态构造函数。

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

泛型类中的方法本身可以是泛型；非泛型方法是由类的类型参数进行隐式参数化。

以下特殊规则适用于泛型类中的方法：

- 泛型类中的方法可以将类型参数用作参数、返回类型或本地变量。

- 泛型类中的方法可以将开放式或封闭式构造类型用作参数、返回类型或本地变量。

### <a name="non-generic-methods-in-generic-classes"></a>泛型类中的非泛型方法

泛型类中没有附加类型参数的方法通常称为“非泛型方法”，尽管它们是由封闭式泛型类进行隐式参数化。

非泛型方法的签名可以包含封闭类的一个或多个类型参数，可以是直接包含，也可以是包含在开放式构造类型中。 例如：

`void MyMethod(MyClass<ItemType> x) {}`

此类方法的主体也可以使用这些类型参数。

## <a name="example"></a>示例

下面的示例在泛型类 `MyClass<ItemType>` 中声明非泛型方法 `ProtectData`。 此方法在签名中使用类的类型参数 `ItemType`（包含在开放式构造类型中）。

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

在泛型类和非泛型类中，都可以声明泛型方法。 例如：

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

虽然从由类的类型参数进行参数化的意义上来说，非泛型方法仍是泛型的，但它没有其他任何类型参数。

泛型类中的所有类型方法都可以是泛型的，包括静态方法、实例方法和虚方法。

## <a name="example"></a>示例

下面的示例展示了如何在泛型类中声明和使用泛型方法：

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

## <a name="using-nested-types-in-generic-classes"></a>在泛型类中使用嵌套类型

就像普通类一样，可以在泛型类中声明其他类型。 嵌套类声明是由外部类声明的类型参数进行隐式参数化。 因此，每个构造外部类型都定义有不同的嵌套类。 例如，在下面的声明中，

```cpp
// generic_classes_5.cpp
// compile with: /clr /c
generic <typename ItemType>
ref struct Outer {
   ref class Inner {};
};
```

类型 `Outer<int>::Inner` 与类型 `Outer<double>::Inner` 不同。

与泛型类中的泛型方法一样，可以为嵌套类型定义其他类型参数。 如果你在内部类和外部类中使用相同的类型参数名称，内部类型参数会隐藏外部类型参数。

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

由于没有办法引用外部类型参数，因此编译器会在这种情况下生成警告。

在构造嵌套泛型类型已命名后，内部类型的类型参数列表中不包括外部类型的类型参数，尽管内部类型是由外部类型的类型参数进行隐式参数化。 在上面的示例中，构造类型的名称应为 `Outer<int>::Inner<string>`。

下面的示例展示了如何使用泛型类中的嵌套类型生成和读取链接列表。

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

## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>泛型类中的属性、事件、索引器和运算符

- 属性、事件、索引器和运算符可以使用封闭泛型类的类型参数作为返回值、参数或本地变量（比如在 `ItemType` 是类的类型参数时）：

    ```cpp
    public ItemType MyProperty {}
    ```

- 属性、事件、索引器和运算符本身无法参数化。

## <a name="example"></a>示例

下面的示例展示了泛型类中实例属性的声明。

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

下面的示例展示了含事件的泛型类。

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

泛型结构的声明和使用规则与泛型类相似，区别如 Visual C++ 语言参考中所述。

## <a name="example"></a>示例

下面的示例声明一个泛型结构，其中 `MyGenStruct` 包含一个字段， `myField` 并将不同类型（ **`int`** 、、）的值分配 **`double`** `String^` 给此字段。

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

[泛型](generics-cpp-component-extensions.md)
