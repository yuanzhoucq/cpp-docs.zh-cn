---
title: "interior_ptr (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "stdcli::language::interior_ptr"
  - "interior_ptr_cpp"
  - "interior_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interior_ptr 关键字 [C++]"
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# interior_ptr (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*内部指针* 声明一个指向的指针在引用类型中，但不为对象。  钉住指针可以指向句柄引用、值类型或装箱类型的托管类型的句柄、成员或托管数组的元素。  
  
## 所有运行时  
 （无适用于所有运行时的语言功能的备注。）  
  
## Windows Runtime — Windows 运行时  
 \(此语言功能没有只适用于 Windows 运行时的备注。）  
  
### 要求  
 编译器选项：**\/ZW**  
  
## 公共语言运行时  
 以下语法示例演示内部指针。  
  
### 语法  
  
```cpp  
cli::interior_ptr<cv_qualifier type> var = &initializer;  
```  
  
### 参数  
 *cv\_qualifier*  
 **const** 或 `volatile` 限定符。  
  
 *type*  
 *initializer* 的类型。  
  
 *var*  
 `interior_ptr` 变量的名称。  
  
 *initializer*  
 引用类型元素，托管数组，或者任何其他的成员可以分配给本机指针的对象。  
  
### 备注  
 本机指针无法跟踪项，因为其位置对托管堆更改，由对象进行垃圾回收器移动该实例。  为了正确引用的指针可以实例，运行时需要更新指针到新标识的对象。  
  
 `interior_ptr` 表示本机指针的功能扩展。因此，可以分配给本机指针的任何也可以分配给 `interior_ptr`。内部指针允许运行同一组操作与本机指针，其中包括比较和指针算法。  
  
 内部指针在堆栈上只能声明。内部指针无法声明为类的成员。  
  
 由于是内部指针在堆栈仅存在，将内部指针的地址为非托管指针。  
  
 `interior_ptr` 包含对 `bool`的隐式转换，所以允许其在条件语句的用法。  
  
 有关如何声明点为对象在垃圾回收堆无法移动的内部指针的信息，请参见 [pin\_ptr](../windows/pin-ptr-cpp-cli.md)。  
  
 `interior_ptr` 在 cli 命名空间中。有关更多信息，请参见[Platform、default 和 cli 命名空间](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
 有关内部指针的更多信息，请参见  
  
-   [如何：声明和使用内部指针及托管数组 \(C\+\+\/CLI\)](../windows/how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)  
  
-   [如何：用 interior\_ptr 关键字声明值类型 \(C\+\+\/CLI\)](../windows/how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)  
  
-   [如何：用内部指针和本机指针重载函数 \(C\+\+\/CLI\)](../windows/how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)  
  
-   [如何：用 const 关键字声明内部指针 \(C\+\+\/CLI\)](../windows/how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 下面的示例演示如何声明和使用内部指针为引用类型。  
  
```cpp  
// interior_ptr.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyClass {  
public:  
   int data;  
};  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;  
   h_MyClass->data = 1;  
   Console::WriteLine(h_MyClass->data);  
  
   interior_ptr<int> p = &(h_MyClass->data);  
   *p = 2;  
   Console::WriteLine(h_MyClass->data);  
  
   // alternatively  
   interior_ptr<MyClass ^> p2 = &h_MyClass;  
   (*p2)->data = 3;  
   Console::WriteLine((*p2)->data);  
}  
```  
  
 **Output**  
  
 **1**   
**2**   
**3**   
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)