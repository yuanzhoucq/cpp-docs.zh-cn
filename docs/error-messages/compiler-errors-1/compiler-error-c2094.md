---
title: "编译器错误 C2094 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2094"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2094"
ms.assetid: 9e4f8f88-f189-46e7-91c9-481bacc7af87
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2094
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标签“identifier”未定义  
  
 通过 [goto](../Topic/goto%20\(C%23%20Reference\).md) 语句使用的标签在函数中不存在。  
  
 以下示例生成 C2094：  
  
```  
// C2094.c int main() { goto test; }   // C2094  
```  
  
 可能的解决方法：  
  
```  
// C2094b.c int main() { goto test; test: { } }  
```