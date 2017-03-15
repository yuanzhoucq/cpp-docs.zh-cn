---
title: "编译器警告 （等级 1） C4838 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4838
dev_langs:
- C++
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 227af1840fe5aee63545e35456fe09749f00de1d
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4838"></a>编译器警告 （等级 1） C4838
从 type_1 转换到 type_2 所需收缩转换  
  
 使用聚合或列表初始化时找到的隐式收缩转换。  
  
 C 语言允许隐式收缩转换赋值和初始化，并且 c + + 遵循一种花色，即使意外收缩是太多的代码错误的原因。 若要使代码更安全，c + + 标准要求的初始化列表中的收缩转换发生时诊断消息。 Visual c + + 中在诊断处于[编译器错误 C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md)时使用支持从 Visual Studio 2015 中的统一初始化语法。 编译器将生成警告 C4838 时使用列表或 Visual Studio 2013 支持聚合初始化语法。  
  
 当您知道可能转换后的值的范围可以在目标中容纳不下时，收缩转换可以是没有问题。 在这种情况下，您知道个以上的编译器会完成。 如果您有意进行收缩转换，在您的意图明确使用静态强制转换。 否则，此警告消息几乎总是指示在代码中出现了 bug。 您可以通过确保您初始化的对象具有足够大以处理输入的类型，从而解决它。  
  
 下面的示例生成 C4838 并演示一种方法，以修复此错误︰  
  
```  
// C4838.cpp -- C++ narrowing conversion diagnostics  
// Compile by using: cl /EHsc C4838.cpp  
  
struct S1 {  
    int m1;  
    double m2, m3;  
};  
  
void function_C4838(double d1) {  
    double ad[] = { 1, d1 }; // OK  
    int ai[] = { 1, d1 };    // warning C4838  
    S1 s11 = { 1, 2, d1 };   // OK  
    S1 s12 { d1, 2, 3 };     // warning C4838  
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838  
}  
```
