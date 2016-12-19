---
title: "编译器错误 C2075 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2075"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2075"
ms.assetid: 8b1865d2-540b-4117-b982-e7a58a0b6cf7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2075
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：数组初始化需要大括号  
  
 指定的数组两边没有大括号。  
  
 以下示例生成 C2075：  
  
```  
// C2075.c int main() { int i[] = 1, 2, 3 };   // C2075 }  
```  
  
 可能的解决方法：  
  
```  
// C2075b.c int main() { int j[] = { 1, 2, 3 }; }  
```