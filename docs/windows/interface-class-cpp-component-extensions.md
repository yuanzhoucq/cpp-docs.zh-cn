---
title: 接口类 （c + + 组件扩展） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- interface_CPP
dev_langs:
- C++
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74b4ea6b82de65f691d5d0350e161725625e4e1f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604481"
---
# <a name="interface-class--c-component-extensions"></a>接口类（C++ 组件扩展）
声明接口。  有关本机接口的信息，请参阅[__interface](../cpp/interface.md)。  
  
## <a name="all-runtimes"></a>所有运行时  

### <a name="syntax"></a>语法  
  
```  
interface_access  
interface class  
 name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};  
```  
  
### <a name="parameters"></a>参数  
  
 *interface_access*  
 在程序集外部接口的可访问性。  可能的值为**公共**并**专用**。  **专用**是默认值。 不能具有嵌套的接口*interface_access*说明符。  
  
 *name*  
 接口的名称。  
  
 *inherit_access*  
 可访问性*base_interface*。  唯一允许的可访问性的基接口是**公共**（默认值）。  
  
 *base_interface* （可选）  
 接口的基接口*名称*。  
  
### <a name="remarks"></a>备注  
  
 **接口结构**等效于**接口类**。  
  
 接口可以包含函数、 事件和属性的声明。  所有接口成员都具有公共可访问性。 接口还可以包含静态数据成员、 函数、 事件和属性，并且必须在接口中定义这些静态成员。  
  
 接口定义可能会如何实现一个类。 接口不是类和类只能实现接口。 一个类定义在接口中声明的函数，被实现该函数，不重写。 因此，名称查找不包括接口成员。  
  
 类或派生接口的结构必须实现接口的所有成员。 实现接口时*名称*还必须实现的接口中`base_interface`列表。  
  
 有关详细信息，请参见:  
  
-   [接口静态构造函数](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)  
  
-   [泛型接口 (Visual C++)](../windows/generic-interfaces-visual-cpp.md)  
  
 有关其他 CLR 类型的信息，请参阅[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 您可以在编译时检测类型是否具有的接口`__is_interface_class(type)`。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 在开发环境中，你可以获取的 F1 帮助上这些关键字通过突出显示关键字 (`interface class`，例如)，然后按 F1。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 **备注**  
  
 (此语言功能没有只适用于 Windows 运行时的备注。）  
  
### <a name="requirements"></a>要求  
 编译器选项：`/ZW`  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **备注**  
  
 （此语言功能没有只适用于公共运行时的备注。）  
  
### <a name="requirements"></a>要求  
 编译器选项：`/clr`  
  
### <a name="examples"></a>示例  
  
 下面的代码示例演示如何一个接口可定义时钟函数的行为。  
  
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
  
 **输出**  
  
```Output  
in Function_3  
  
in Function_2  
  
in Function_1  
  
8  
  
OnClick: 7, 3.14159  
  
in Function_1  
```  
  
 下面的代码示例演示两种方式使用相同的签名声明在多个接口，这些接口由一个类实现的函数。  
  
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
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)