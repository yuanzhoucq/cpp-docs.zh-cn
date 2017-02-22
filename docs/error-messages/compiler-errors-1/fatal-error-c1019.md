---
title: "错误 C1019 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1019"
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 错误 C1019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

意外的 \#else  
  
 `#else` 指令出现在 `#if`、`#ifdef` 或 `#ifndef` 构造外部。 仅在这些构造之一中使用 `#else`。  
  
 下面的示例生成 C1019：  
  
```  
// C1019.cpp #else   // C1019 #endif int main() {}  
```  
  
 可能的解决方法：  
  
```  
// C1019b.cpp #if 1 #else #endif int main() {}  
```