---
title: "错误 C1018 | Microsoft Docs"
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
  - "C1018"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1018"
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1018
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

意外的 \#elif  
  
 `#elif` 指令出现在 `#if`、`#ifdef` 或 `#ifndef` 构造外部。 仅在这些构造之一中使用 `#elif`。  
  
 下面的示例生成 C1018：  
  
```  
// C1018.cpp #elif      // C1018 #endif int main() {}  
```  
  
 可能的解决方法：  
  
```  
// C1018b.cpp #if 1 #elif #endif int main() {}  
```