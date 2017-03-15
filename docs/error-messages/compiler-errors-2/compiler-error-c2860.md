---
title: "编译器错误 C2860 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2860"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2860"
ms.assetid: ccc83553-90ed-4e94-b5e9-38b58ae38e31
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2860
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“void”不能是参数类型，“\(void\)”除外  
  
 类型 `void` 无法与其他参数一起用作参数类型。  
  
 下面的示例生成 C2860：  
  
```  
// C2860.cpp  
// compile with: /c  
void profunc1(void, int i);   // C2860  
void func10(void);   // OK  
```