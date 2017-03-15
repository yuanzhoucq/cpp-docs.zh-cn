---
title: "编译器错误 C3532 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3532"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3532"
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3532
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”:“auto”的用法不正确  
  
 不能使用 `auto` 关键字声明指定的类型。  例如，不能使用 `auto` 关键字声明数组或方法返回类型。  
  
### 更正此错误  
  
1.  确保初始化表达式的结果是有效类型。  
  
2.  确保不声明数组或方法返回类型。  
  
## 示例  
 下面的示例会产生 C3532，因为 `auto` 关键字不能声明方法返回类型。  
  
```  
// C3532a.cpp  
// Compile with /Zc:auto  
auto f(){}   // C3532  
```  
  
## 示例  
 下面的示例会产生 C3532，因为 `auto` 关键字不能声明数组。  
  
```  
// C3532b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int x[5];  
   auto a[5];            // C3532  
   auto b[1][2];         // C3532  
   auto y[5] = x;        // C3532  
   auto z[] = {1, 2, 3}; // C3532  
   auto w[] = x;         // C3532  
   return 0;  
}  
```  
  
## 请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)