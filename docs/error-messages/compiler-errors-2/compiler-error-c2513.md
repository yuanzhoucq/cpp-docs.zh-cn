---
title: "编译器错误 C2513 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2513
dev_langs: C++
helpviewer_keywords: C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 62c55a1a6eb093d4ef6921f6d0f8b7c50683ff8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2513"></a>编译器错误 C2513
type: = 之前的任何变量声明  
  
 类型说明符出现在不带任何变量的标识符的声明。  
  
 下面的示例生成 C2513:  
  
```  
// C2513.cpp  
int main() {  
   int = 9;   // C2513  
   int i = 9;   // OK  
}  
```  
  
 此错误还可能来自于为 Visual Studio.NET 2003年执行的编译器一致性工作： 不再允许的 typedef 的初始化。 Typedef 的初始化不允许使用由标准，并且现在将生成编译器错误。  
  
```  
// C2513b.cpp  
// compile with: /c  
typedef struct S {  
   int m_i;  
} S = { 1 };   // C2513  
// try the following line instead  
// } S;  
```  
  
 一种替代方法是删除`typedef`定义的变量聚合初始值设定项列表，但这不建议，因为它将创建具有相同名称作为类型的变量和隐藏的类型名称。