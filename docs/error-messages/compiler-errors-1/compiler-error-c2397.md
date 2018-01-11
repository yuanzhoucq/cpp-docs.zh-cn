---
title: "编译器错误 C2397 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2397
dev_langs: C++
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 315d375524884ec987fea747b1d3c20f2ad56173
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2397"></a>编译器错误 C2397
从 type_1 类型到 type_2 转换需要收缩转换  
  
 使用统一初始化时找到的隐式收缩转换。  
  
 C 语言允许在分配和初始化，隐式收缩转换和 c + + 遵循适合，即使意外收缩是许多代码错误的原因。 若要使代码更加安全，标准 c + + 需要收缩转换发生在初始化列表中时诊断消息。 在 Visual c + +，诊断是编译器错误 C2397 在 Visual Studio 2015 中使用统一安装支持的语法开头时。 编译器将生成[编译器警告 （等级 1） C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md)时使用的列表或支持的 Visual Studio 2013 的聚合初始化语法。  
  
 当你知道目标中可以容纳该值可能的转换后的值范围时，可以认为可以收缩转换。 在这种情况下，你知道个以上的编译器执行的操作。 如果你有意进行收缩转换，你的意图显式使用进行静态强制转换。 否则，此错误消息几乎始终表示在代码中出现了 bug。 可以通过确保你初始化的对象具有足够大以处理输入的类型，从而修复此错误。  
  
 下面的示例生成 C2397，并演示修复此错误的一种方法：  
  
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