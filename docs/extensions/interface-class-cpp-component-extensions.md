---
title: interface class（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- interface_CPP
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
ms.openlocfilehash: 60e8965e3ef2538554d8c664b35bd0849bd5e69e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515702"
---
# <a name="interface-class--ccli-and-ccx"></a>interface class（C++/CLI 和 C++/CX）

声明接口。  若要了解本机接口，请参阅 [__interface](../cpp/interface.md)。

## <a name="all-runtimes"></a>所有运行时

### <a name="syntax"></a>语法

```cpp
interface_access
interface class
name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};
```

### <a name="parameters"></a>参数

interface_access<br/>
程序集外部接口的可访问性。  可取值为 public 和 private。  private 是默认值。 嵌套接口不得包含 interface_access 说明符。

*name*<br/>
接口的名称。

inherit_access<br/>
base_interface 的可访问性。  唯一允许的基接口可访问性是 public（默认值）。

base_interface<br/>
（可选）接口 name 的基接口。

### <a name="remarks"></a>备注

interface struct 相当于 interface class。

接口可以包含函数、事件和属性的声明。  所有接口成员都有 public 可访问性。 接口还可以包含静态数据成员、函数、事件和属性，必须在接口中定义这些静态成员。

接口定义类的实现方式。 接口不是类，类只能实现接口。 如果类定义接口中声明的函数，函数会实现，但不会被重写。 因此，名称查找不包括接口成员。

派生自接口的类或结构必须实现接口的所有成员。 实现接口 name 时，还必须实现 `base_interface` 列表中的接口。

有关详细信息，请参见:

- [接口静态构造函数](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

- [泛型接口 (C++/CLI)](generic-interfaces-visual-cpp.md)

若要了解其他 CLR 类型，请参阅[类和结构](classes-and-structs-cpp-component-extensions.md)。

在编译时，可以使用 `__is_interface_class(type)` 来检测类型是否是 interface。 有关详细信息，请参阅[编译器对类型特征的支持](compiler-support-for-type-traits-cpp-component-extensions.md)。

在开发环境中，可以突出显示关键字（例如 `interface class`）并按 F1，从而获取这些关键字的 F1 帮助。

## <a name="windows-runtime"></a>Windows 运行时

### <a name="remarks"></a>备注

(此语言功能没有只适用于 Windows 运行时的备注。）

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="remarks"></a>备注

（此语言功能没有只适用于公共运行时的备注。）

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的代码示例展示了接口如何定义时钟函数的行为。

```cpp
// mcppv2_interface_class.cpp
// compile with: /clr
using namespace System;

public delegate void ClickEventHandler(int, double);

// define interface with nested interface
public interface class Interface_A {
   void Function_1();

   interface class Interface_Nested_A {
      void Function_2();
   };
};

// interface with a base interface
public interface class Interface_B : Interface_A {
   property int Property_Block;
   event ClickEventHandler^ OnClick;
   static void Function_3() { Console::WriteLine("in Function_3"); }
};

// implement nested interface
public ref class MyClass : public Interface_A::Interface_Nested_A {
public:
   virtual void Function_2() { Console::WriteLine("in Function_2"); }
};

// implement interface and base interface
public ref class MyClass2 : public Interface_B {
private:
   int MyInt;

public:
   // implement non-static function
   virtual void Function_1() { Console::WriteLine("in Function_1"); }

   // implement property
   property int Property_Block {
      virtual int get() { return MyInt; }
      virtual void set(int value) { MyInt = value; }
   }
   // implement event
   virtual event ClickEventHandler^ OnClick;

   void FireEvents() {
      OnClick(7, 3.14159);
   }
};

// class that defines method called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }
};

int main() {
   // call static function in an interface
   Interface_B::Function_3();

   // instantiate class that implements nested interface
   MyClass ^ x = gcnew MyClass;
   x->Function_2();

   // instantiate class that implements interface with base interface
   MyClass2 ^ y = gcnew MyClass2;
   y->Function_1();
   y->Property_Block = 8;
   Console::WriteLine(y->Property_Block);

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   y->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // invoke events
   y->FireEvents();

   // unhook handler to event
   y->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // call implemented function via interface handle
   Interface_A^ hi = gcnew MyClass2();
   hi->Function_1();
}
```

```Output
in Function_3

in Function_2

in Function_1

8

OnClick: 7, 3.14159

in Function_1
```

下面的代码示例展示了两种方法来实现签名相同的函数，这些函数在多个接口中声明，而这些接口又被一个类使用。

```cpp
// mcppv2_interface_class_2.cpp
// compile with: /clr /c
interface class I {
   void Test();
   void Test2();
};

interface class J : I {
   void Test();
   void Test2();
};

ref struct R : I, J {
   // satisfies the requirement to implement Test in both interfaces
   virtual void Test() {}

   // implement both interface functions with explicit overrides
   virtual void A() = I::Test2 {}
   virtual void B() = J::Test2 {}
};
```

## <a name="see-also"></a>请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)