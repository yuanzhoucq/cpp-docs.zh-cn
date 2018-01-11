---
title: "接口类 （c + + 组件扩展） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: interface_CPP
dev_langs: C++
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: abe4173dabd20442b96c8e5536b040483df4f150
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="interface-class--c-component-extensions"></a>接口类（C++ 组件扩展）
声明接口。  在本机接口上的信息，请参阅[__interface](../cpp/interface.md)。  
  
## <a name="all-runtimes"></a>所有运行时  
 **语法**  
  
```  
  
interface_access  
interface class  
 name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};  
```  
  
 **参数**  
  
 *interface_access*  
 程序集之外的接口的可访问性。  可能的值为**公共**和`private`。  默认为 `private`。  嵌套的接口不能具有*interface_access*说明符。  
  
 *name*  
 接口的名称。  
  
 *inherit_access*  
 可访问性*base_interface*。  唯一允许可访问性基接口为`public`（默认值）。  
  
 *base_interface* （可选）  
 接口的基接口*名称*。  
  
 **备注**  
  
 **接口结构**等效于**接口类**。  
  
 接口可以包含声明的函数、 事件和属性的声明。  所有接口成员都具有公共可访问性。 接口还可以包含静态数据成员、 函数、 事件和属性，并且必须在接口中定义这些静态成员。  
  
 接口定义可能如何实现一个类。 接口不是类和类只能实现接口。 当一个类定义在接口中声明的函数时，该函数实现，不重写。 因此，名称查找不包括接口成员。  
  
 类或派生自接口的结构必须实现该接口的所有成员。 在实现接口时*名称*还必须实现中的在接口`base_interface`列表。  
  
 有关详细信息，请参见:  
  
-   [接口静态构造函数](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)  
  
-   [泛型接口 (Visual C++)](../windows/generic-interfaces-visual-cpp.md)  
  
 有关其他 CLR 类型的信息，请参阅[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 你可以在编译时检测类型是否与接口`__is_interface_class(type)`。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 在开发环境中，你可以获取的 F1 帮助上这些关键字通过突出显示关键字 (`interface class`，例如)，然后按 F1。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 **备注**  
  
 (此语言功能没有只适用于 Windows 运行时的备注。）  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **备注**  
  
 （此语言功能没有只适用于公共运行时的备注。）  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的代码示例演示如何接口可以定义 clock 函数的行为。  
  
```  
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
  
 **输出**  
  
```Output  
in Function_3  
  
in Function_2  
  
in Function_1  
  
8  
  
OnClick: 7, 3.14159  
  
in Function_1  
```  
  
 **示例**  
  
 下面的代码示例演示两种方式使用相同的签名声明在多个接口和类其中使用这些接口实现函数。  
  
```  
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
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)