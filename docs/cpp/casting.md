---
title: "强制转换 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "强制转换"
  - "类 [C++], 多态性"
  - "强迫"
  - "动态强制转换运算符"
  - "多态类"
  - "静态强制转换运算符"
  - "虚函数, 在派生类中"
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 强制转换
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 C\+\+ 语言中，如果类从包含虚函数的基类派生，则指向基类类型的指针可用于调用派生类对象中包含的虚函数的实现。  包含虚函数的类有时被称为“多态类”。  
  
 由于派生类完全包含它派生自的所有基类的定义，因此在类层次结构上将指针转换至这些基类中的任何一个是安全的。  提供一个指向基类的指针，在层次结构中向下转换指针可能是安全的。  如果将指向的对象实际上是从基类派生的类型，则是安全的。  在这种情况下，实际对象称为“完整对象”。指向基类的指针称为指向完整对象的“子对象”。  例如，考虑下图中显示的类层次结构。  
  
 ![类层次结构](../cpp/media/vc38zz1.png "vc38ZZ1")  
类层次结构  
  
 如下图所示，可对类型为 `C` 的对象进行可视化。  
  
 ![具有子对象 B 和 A 的类 C](../cpp/media/vc38zz2.png "vc38ZZ2")  
带有 B 子对象和 A 子对象的类 C  
  
 给定 `C` 类的一个实例，存在 `B` 子对象和 `A` 子对象。  包括 `A` 和 `B` 子对象的 `C` 实例是“完整对象。”  
  
 通过使用运行时类型信息，可以检查指针实际是否指向完整对象，并可以安全转换以指向其层次结构中的另一个对象。  [dynamic\_cast](../cpp/dynamic-cast-operator.md) 运算符可用于进行这些类型的转换。  它还执行必要的运行时检查以确保操作安全。  
  
 对于非多态类型的转换，可以使用 [static\_cast](../cpp/static-cast-operator.md) 运算符（本主题说明静态和动态强制转换之间的差异，以及何时适合使用它们）。  
  
 此节涵盖以下主题：  
  
-   [转换运算符](../cpp/casting-operators.md)  
  
-   [运行时类型信息](../cpp/run-time-type-information.md)  
  
## 请参阅  
 [表达式](../cpp/expressions-cpp.md)