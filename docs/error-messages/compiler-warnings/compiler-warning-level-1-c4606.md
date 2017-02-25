---
title: "编译器警告（等级 1）C4606 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4606"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4606"
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4606
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma 警告: 忽略“warning\_number”；代码分析警告与警告等级无关  
  
 对于代码分析警告，[警告](../../preprocessor/warning.md) 杂注只支持 `error`、`once` 和 `default`。  
  
## 示例  
 下面的示例生成 C4606。  
  
```  
// C4606.cpp  
// compile with: /c /W1  
#pragma warning(1: 6001)   // C4606  
#pragma warning(once: 6001)   // OK  
```