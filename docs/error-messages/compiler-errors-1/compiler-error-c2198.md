---
title: "编译器错误 C2198 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2198"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2198"
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2198
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 用于调用的参数太少  
  
 编译器发现用于函数调用的参数太少或函数声明不正确。  
  
 以下示例生成 C2198：  
  
```  
// C2198.c // compile with: /c void func( int, int ); int main() { func( 1 );   // C2198 only one actual parameter func( 1, 1 );   // OK }  
```