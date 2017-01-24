---
title: "INSTR | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InStr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "INSTR directive"
ms.assetid: fc37f6a2-3c95-47b2-b6bb-1066edd25994
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# INSTR
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

查找 *textitem2* 第一个匹配项 *textitem1 的*。  
  
## 语法  
  
```  
  
name  
 INSTR [[position,]] textitem1, textitem2  
```  
  
## 备注  
 该 *起始位置* 是可选的。  每个文本项可以是一个文本字符串、 `%`后的常数和宏函数返回的字符串。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)