---
title: "委托（C++ 组件扩展） | Microsoft Docs"
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
  - "delegate_cpp"
  - "delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "delegate 关键字 [C++]"
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 委托（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

声明代表函数指针的一种类型。  
  
## 所有运行时  
 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 和公共语言运行时都支持委托。  
  
### 备注  
 `delegate` 是上下文相关的关键字。  有关详细信息，请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
 要在编译时检测该类型是否为委托，请使用 `__is_delegate()` 类型特征。  有关详细信息，请参阅[编译器使用类型特征支持](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
## Windows Runtime — Windows 运行时  
 C\+\+\/CX 支持具有以下语法的委托。  
  
### 语法  
  
```cpp  
  
access delegate return-type delegate-type-identifier ([ parameters ])  
```  
  
### 参数  
 *access*  
 （可选）委托的可访问性可以是 `public`（默认值）或 `private`。  带 `const` 或 `volatile` 关键字的函数原型也将得到限定。  
  
 *return\-type*  
 函数原型的返回类型。  
  
 *delegate\-type\-identifier*  
 声明的委托类型名称。  
  
 *parameters*  
 （可选）函数原型的类型和标识符。  
  
### 备注  
 使用*委托类型标识符delegate\-type\-identifier*声明事件，该事件的原型与委托相同。  有关更多信息，请参见[委托 \(C\+\+\/CX\)](../Topic/Delegates%20\(C++-CX\).md)。  
  
### 要求  
 编译器选项：**\/ZW**  
  
## 公共语言运行时  
 公共语言运行时支持具有以下语法的委托。  
  
### 语法  
  
```cpp  
  
access delegate function_declaration  
```  
  
### 参数  
 *access*  
 （可选）程序集外部委托的可访问性可以是公共或私有的。默认为 private。在选件类中，委托可以具有任何可访问性。  
  
 *function\_declaration*  
 可与委托绑定的函数签名。  委托的返回类型可以是任何托管类型。  考虑到互操作性，建议委托的返回类型是 CLS 类型。  
  
 要定义一个未绑定的委托，*function\_declarationfunction\_declaration* 中的第一个参数应为对象的 `this` 指针类型。  有关详细信息，请参阅[未绑定的委托](../misc/unbound-delegates.md)。  
  
### 备注  
 委托是多路广播：“函数指针”可绑定到一或多个托管类中的方法。  **委托**关键字以特定方法签名定义多路广播委托类型。  
  
 委托还可绑定到值类方法，例如静态方法。  
  
 委托具有下面的特性：  
  
-   它继承自 **System::MulticastDelegate**。  
  
-   它有一个带两个参数的构造函数：指向托管类或 **NULL** 的指针（绑定到静态方法时）和指定类型的完全限定方法。  
  
-   它具有一个称为 `Invoke` 的方法，其签名与委托的声明签名匹配。  
  
 调用委托时，将按其附加顺序调用其函数。  
  
 委托的返回值是来自其最后附加的成员函数的返回值。  
  
 无法重载委托。  
  
 委托可绑定或不绑定。  
  
 实例化一个绑定委托时，第一个参数应为对象引用。委托实例化的第二参数可以是托管类对象方法的地址，或者指向值类型方法的指针。委托实例化的第二参数必须命名带完全类范围语法的方法并应用运算符地址。  
  
 实例化一个未绑定委托时，第一个参数应为托管类对象方法的地址或指向值类型方法的指针。参数必须通过完全类范围语法进行命名并应用运算符地址。  
  
 为静态或全局函数创建委托时，仅需要一个参数：函数（可选，函数的地址）。  
  
 有关委托的更多信息，请参见  
  
-   [未绑定的委托](../misc/unbound-delegates.md)  
  
-   [如何：定义和使用委托](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)  
  
-   [委托给值类成员](../misc/how-to-associate-delegates-to-members-of-a-value-class.md)  
  
-   [未托管的函数的委托](../misc/how-to-associate-delegates-to-unmanaged-functions.md)  
  
-   [组成的委托](../misc/how-to-compose-delegates.md)  
  
-   [如何：将委托传递到预期有函数指针的本机函数](../misc/how-to-pass-a-delegate-hat-to-a-native-function-expecting-a-function-pointer.md)  
  
-   [泛型委托](../windows/generic-delegates-visual-cpp.md)  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 以下示例显示了如何声明、初始化和调用委托。  
  
```cpp  
// mcppv2_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare a delegate  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      Console::WriteLine("in func1 {0}", i);  
   }  
  
   void func2(int i) {  
      Console::WriteLine("in func2 {0}", i);  
   }  
  
   static void func3(int i) {  
      Console::WriteLine("in static func3 {0}", i);  
   }  
};  
  
int main () {  
   A ^ a = gcnew A;  
  
   // declare a delegate instance  
   MyDel^ DelInst;  
  
   // test if delegate is initialized  
   if (DelInst)  
      DelInst(7);  
  
   // assigning to delegate  
   DelInst = gcnew MyDel(a, &A::func1);  
  
   // invoke delegate  
   if (DelInst)  
      DelInst(8);  
  
   // add a function  
   DelInst += gcnew MyDel(a, &A::func2);  
  
   DelInst(9);  
  
   // remove a function  
   DelInst -= gcnew MyDel(a, &A::func1);  
  
   // invoke delegate with Invoke  
   DelInst->Invoke(10);  
  
   // make delegate to static function  
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);  
   StaticDelInst(11);  
}  
```  
  
 **Output**  
  
  **在 func1 8 中**  
 **在 func1 9 中**  
 **在 func2 9 中**  
 **在 func2 10 中**  
 **在静态 func3 11 中**   
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)