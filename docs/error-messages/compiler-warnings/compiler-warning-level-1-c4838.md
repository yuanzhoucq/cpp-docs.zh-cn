---
title: "编译器警告 （等级 1） C4838 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4838
dev_langs: C++
helpviewer_keywords: C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76002ebf0a6ac6e610b1fcd10d02fab49287495b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4838"></a>编译器警告 （等级 1） C4838
从 type_1 类型到 type_2 转换需要收缩转换  
  
 使用聚合或列表初始化时找到的隐式收缩转换。  
  
 C 语言允许在分配和初始化，隐式收缩转换和 c + + 遵循适合，即使意外收缩是许多代码错误的原因。 若要使代码更加安全，标准 c + + 需要收缩转换发生在初始化列表中时诊断消息。 在 Visual c + +，诊断是[编译器错误 C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md)使用统一初始化语法时支持从 Visual Studio 2015 开始。 编译器将生成警告 C4838 时使用的列表或支持的 Visual Studio 2013 的聚合初始化语法。  
  
 当你知道目标中可以容纳该值可能的转换后的值范围时，可以认为可以收缩转换。 在这种情况下，你知道个以上的编译器执行的操作。 如果你有意进行收缩转换，你的意图显式使用进行静态强制转换。 否则，此警告消息几乎始终指示在代码中出现了 bug。 可以通过确保你初始化的对象具有足够大以处理输入的类型，从而修复此错误。  
  
 下面的示例生成 C4838，并演示修复此错误的一种方法：  
  
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