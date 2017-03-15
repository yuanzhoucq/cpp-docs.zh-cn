---
title: "编译器警告（等级 1）C4739 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4739"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4739"
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 1）C4739
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对变量“var”的引用超过了其存储空间  
  
 将值赋给了变量，但是该值的大小超过变量的大小。 内存将写入变量的内存位置之外，并且可能丢失数据。  
  
 要消除此警告，仅需将值赋给其大小可容纳该值的变量。  
  
 下面的示例生成 C4739：  
  
```  
// C4739.cpp // compile with: /RTCs /Zi /W1 /c char *pc; int main() { char c; *(int *)&c = 1;   // C4739 // OK *(char *)&c = 1; }  
```