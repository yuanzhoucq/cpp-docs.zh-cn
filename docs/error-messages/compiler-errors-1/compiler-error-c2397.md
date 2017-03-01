---
title: "编译器错误 C2397 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2397
dev_langs:
- C++
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 31f2b548fd13bc7702d44ef4a6d5dc5c34a5eb3c
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2397"></a>编译器错误 C2397
从 type_1 转换到 type_2 所需收缩转换  
  
 使用统一初始化时找到的隐式收缩转换。  
  
 C 语言允许隐式收缩转换赋值和初始化，并且 c + + 遵循一种花色，即使意外收缩是太多的代码错误的原因。 若要使代码更安全，c + + 标准要求的初始化列表中的收缩转换发生时诊断消息。 Visual c + + 中诊断是在 Visual Studio 2015 中使用统一初始化支持的语法开头编译器错误 C2397。 编译器将生成[编译器警告 （等级 1） C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md)时使用列表或 Visual Studio 2013 支持聚合初始化语法。  
  
 当您知道可能转换后的值的范围可以在目标中容纳不下时，收缩转换可以是没有问题。 在这种情况下，您知道个以上的编译器会完成。 如果您有意进行收缩转换，在您的意图明确使用静态强制转换。 否则，此错误消息几乎总是指示在代码中出现了 bug。 您可以通过确保您初始化的对象具有足够大以处理输入的类型，从而解决它。  
  
 下面的示例生成 C2397 并演示一种方法，以修复此错误︰  
  
```  
// C2397.cpp -- C++ narrowing conversion diagnostics  
// Compile by using: cl /EHsc C2397.cpp  
#include <vector>   
  
struct S1 {  
    int m1;  
    double m2, m3;  
};  
  
void function_C2397(double d1) {  
    char c1 { 127 };          // OK  
    char c2 { 513 };          // error C2397  
  
    std::vector<S1> vS1;  
    vS1.push_back({ d1, 2, 3 }); // error C2397  
  
    // Possible fix if you know d1 always fits in an int  
    vS1.push_back({ static_cast<int>(d1), 2, 3 });   
}  
```
