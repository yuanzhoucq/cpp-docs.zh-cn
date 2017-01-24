---
title: "接口类（C++ 组件扩展） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "interface_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interface class 关键字"
  - "interface struct 关键字"
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
caps.latest.revision: 30
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 接口类（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

声明接口。 有关托管接口的信息，请参阅[接口类](../cpp/interface.md)。  
  
## 所有运行时  
 **语法**  
  
```  
  
        interface_access interface class  name :  inherit_access base_interface {};  
interface_access interface struct name :  inherit_access base_interface {};  
```  
  
 **参数**  
  
 *interface\_access*  
 一个接口的可访问性在程序集之外的。可能的值为 **public** 和 `private` （`private` 是默认的）。嵌套的接口不能有 *interface\_access* 说明符。  
  
 *name*  
 接口名。  
  
 *inherit\_access*  
 *base\_interface* 可访问性。基本接口中唯一允许的可访问性为 `public` \(默认值\)。  
  
 *base\_interface*（可选）  
 接口的一个基接口。*name*  
  
 **备注**  
  
 **interface struct** 与 **接口类**等效。  
  
 接口可以包含函数、事件和属性的声明。所有接口成员具有公共可访问性。  接口也可以包含静态数据成员、函数、事件和属性，并且，这些静态成员在接口必须定义。  
  
 Interfaces 定义类所能实现如何。  接口不是类，而类仅能实现接口。  当类中定义接口中声明的函数，则函数实现，未被重写。  因此，该名称包含不查找接口成员。  
  
 继承自接口的类必须实现接口成员。  当实现接口 *时名称* 还必须在 `base_interface` 中实现接口会列出。  
  
 有关详细信息，请参阅：  
  
-   [接口静态构造函数](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)  
  
-   [泛型接口 \(Visual C\+\+\)](../windows/generic-interfaces-visual-cpp.md)  
  
 有关其他 CLR 类型的信息，请参见 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 可以检测编译时类型是否与 `__is_interface_class(``type``)`的接口。  有关详细信息，请参阅[编译器使用类型特征支持](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 在开发环境中，您可通过高亮关键字，获取这些关键字的 F1 帮助（例如 `interface class`）。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **备注**  
  
 \(此语言功能没有只适用于 Windows 运行时的备注。）  
  
### 要求  
 编译器选项：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **备注**  
  
 （此语言功能没有只适用于公共运行时的备注。）  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 下面的代码示例演示对接口如何定义时钟函数的行为。  
  
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
  
 **Output**  
  
  **在Function\_3**  
 **在Function\_2**  
 **在Function\_1**  
 **8**  
 **OnClick:7，3.14159**  
 **在Function\_1** **示例**  
  
 下面的代码示例演示两种方法来实现具有多个在接口声明相同的签名的函数，类的位置使用这些接口。  
  
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
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)