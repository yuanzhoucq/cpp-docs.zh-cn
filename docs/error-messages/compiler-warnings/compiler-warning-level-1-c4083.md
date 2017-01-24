---
title: "编译器警告（等级 1）C4083 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4083"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4083"
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4083
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

应输入“token”；找到标识符“identifier”  
  
 标识符在 **\#pragma** 语句中的位置不正确。  
  
## 示例  
  
```  
// C4083.cpp  
// compile with: /W1 /LD  
#pragma warning disable:4083    // C4083  
#pragma warning(disable:4083)   //correct  
```  
  
 检查 [\#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) 指令的语法。