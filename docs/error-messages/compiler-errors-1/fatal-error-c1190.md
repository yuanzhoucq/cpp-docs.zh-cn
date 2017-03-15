---
title: "错误 C1190 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1190"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1190"
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# 错误 C1190
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

托管目标代码需要“\/clr”选项  
  
 你当前使用的是 CLR 构造，但未指定 **\/clr**。  
  
 有关更多信息，请参见[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 下面的示例生成 C1190：  
  
```  
// C1190.cpp // compile with: /c __gc class A {};   // C1190 ref class A {};  
```