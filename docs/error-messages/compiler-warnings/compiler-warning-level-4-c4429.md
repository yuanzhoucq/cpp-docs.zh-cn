---
title: "编译器警告（等级 4）C4429 | Microsoft Docs"
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
  - "C4429"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4429"
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4429
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通用字符名称可能不完整或格式不正确  
  
 编译器检测到格式可能不正确的通用字符名称的字符序列。  通用字符名称是后面跟四个十六进制数字的 `\u`，或后面跟八个十六进制数字的 `\U`。  
  
 下面的示例生成 C4429：  
  
```  
// C4429.cpp  
// compile with: /W4 /WX  
int \ug0e4 = 0;   // C4429  
// Try the following line instead:  
// int \u00e4 = 0;   // OK, a well-formed universal character name.  
```