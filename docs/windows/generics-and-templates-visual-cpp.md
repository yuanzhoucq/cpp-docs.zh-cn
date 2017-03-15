---
title: "型和模板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "普通 [C++], 使用模板"
  - "模板, C++"
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 型和模板
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\# 泛型和 C\+\+ 模板都是用于提供参数化类型支持的语言功能。  但是，它们不同且具有的不同用法。  本主题提供不同类型的概述。  
  
 有关更多信息，请参见[Windows 运行时和托管模板](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)和[模板概述](../Topic/Templates%20Overview.md)。  
  
## 比较泛型和模板  
 C\+\+ 模板和 C\# 泛型之间的区别 \(C\#\)  
  
-   泛型是泛型，直到替换类型将重写运行时。  模板在编译时专用，因此仍不是参数化类型在运行时  
  
-   公共语言运行时 \(CLR\) 专门支持在 MSIL 的泛型。  由于运行时知道泛型，特定类型可以替换泛型类型上重写，当引用包含泛型类型的程序集。  模板，相反，普通类型解析到在编译时，得到的类型不可以从中特殊化其他程序集。  
  
-   具有相同类型参数的两个不同的程序集的专用泛型是同一类型。  具有相同类型参数的两个不同的程序集的专用模板运行时视为不同的类型。  
  
-   生成泛型用作所有引用类型参数使用的可执行代码单个 \(这不可靠。值类型，具有单个实现每个值类型。\)  JIT 编译器知道使用作为类型参数的泛型并可以优化引用或值类型的代码。  模板为每专用化的独立运行时代码。  
  
-   C\# 不允许非类型模板参数，如 `template <int i> C {}`。  模板重命名它们。  
  
-   C\# 不支持显式专用化，即特定类型的模板的自定义实现。  模板  
  
-   C\# 不支持部分专用化：类型参数子集的自定义实现。  模板  
  
-   C\# 不允许将类型参数用作泛型类型的基类。  模板  
  
-   模板支持模板模板参数 \(即  `template<template<class T> class X> class MyClass`\)，而泛型不是。  
  
## 组合泛型和模板  
  
-   在泛型中的基本区别具有生成合并模板和泛型的应用程序的影响。  例如，假定具有一个模板类要创建一般包装用于向该模板为其他语言为泛型。  不能有泛型使然后通过传递到模板类型的参数，该类型参数，因为模板需要具有在编译时，但一般不会解析的类型参数在运行时中  嵌套在泛中的模板不会起作用，因为无法展开模板在能在运行时进行实例化的任意泛型类型的编译时。  
  
## 示例  
  
### 说明  
 下面的示例同时显示了一个简单的示例模板和泛型。  在此示例中，模板类传递参数的泛型类型。  撤消是不可能的。  
  
 可以使用这个，当您与是本地的。Visual C\+\+ 程序集代码的模板时的现有的常规 API 若要生成，或者，如果需要将参数化添加额外的层到泛型类型，利用泛型不支持模板的某些功能。  
  
### 代码  
  
```  
// templates_and_generics.cpp  
// compile with: /clr  
using namespace System;  
  
generic <class ItemType>  
ref class MyGeneric {  
   ItemType m_item;  
  
public:  
   MyGeneric(ItemType item) : m_item(item) {}  
   void F() {   
      Console::WriteLine("F");   
   }  
};  
  
template <class T>  
public ref class MyRef {  
MyGeneric<T>^ ig;  
  
public:  
   MyRef(T t) {  
      ig = gcnew MyGeneric<T>(t);  
      ig->F();  
    }      
};  
  
int main() {  
   // instantiate the template  
   MyRef<int>^ mref = gcnew MyRef<int>(11);  
}  
```  
  
### Output  
  
```  
F  
```  
  
## 请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)