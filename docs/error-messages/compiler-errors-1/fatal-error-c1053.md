---
title: "错误 C1053 | Microsoft Docs"
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
  - "C1053"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1053"
ms.assetid: f50c1c6a-d9cc-42fa-984e-4e2e6e9cd1b1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1053
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“\<identifier\>”：函数太大  
  
 该函数太大，无法编译。  
  
### 使用以下可能的解决方案进行修复  
  
1.  请尝试编译但不优化。  
  
2.  将函数拆分为较小的函数。  
  
3.  减少对内联函数的调用。