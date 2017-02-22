---
title: "编译器警告（等级 1）C4090 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4090"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4090"
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4090
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operation”: 不同的“modifier”限定符  
  
 操作中所使用的变量用指定的修饰符定义，该修饰符防止其在未受编译器检测的情况下被修改。  编译表达式时不进行修改。  
  
 将指向 **const** 或 `volatile` 项的指针赋值给未声明为指向 **const** 或 `volatile` 的指针时，将导致出现此警告。  
  
 该警告针对 C 程序发出。  在 C\+\+ 程序中，编译器发出错误：[C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md)。  
  
 下面的示例生成 C4090：  
  
```  
// C4090.c  
// compile with: /W1  
int *volatile *p;  
int *const *q;  
int **r;  
  
int main() {  
   p = q;   // C4090  
   p = r;  
   q = p;   // C4090  
   q = r;  
   r = p;   // C4090  
   r = q;   // C4090  
}  
```