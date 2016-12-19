---
title: "C 字符常量 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "(') 单引号"
  - "字符, 常量"
  - "常量, 字符"
  - "单引号"
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 字符常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“字符常量”通过在单引号 \(**' '**\) 内封闭可表示的字符集中的单个字符来构成。  字符常量用于表示[执行字符集](../c-language/execution-character-set.md)内的字符。  
  
## 语法  
 *character\-constant*:  
 **'** *c\-char\-sequence* **'**  
  
 **L'** *c\-char\-sequence* **'**  
  
 *c\-char\-sequence*:  
 *c\-char*  
  
 *c\-char\-sequence c\-char*  
  
 *c\-char*:  
 除单引号 \(**'**\)、反斜杠 \(**\\**\) 或者换行符以外的所有源字符集成员  
  
 *escape\-sequence*  
  
 *escape\-sequence*:  
 *simple\-escape\-sequence*  
  
 *octal\-escape\-sequence*  
  
 *hexadecimal\-escape\-sequence*  
  
 *simple\-escape\-sequence*: 一个  
 **\\a \\b \\f \\n \\r \\t \\v**  
  
 **\\' \\" \\\\ \\?**  
  
 *octal\-escape\-sequence*:  
 **\\**  *octal\-digit*  
  
 **\\**  *octal\-digit octal\-digit*  
  
 **\\**  *octal\-digit octal\-digit octal\-digit*  
  
 *hexadecimal\-escape\-sequence*:  
 **\\x**  *hexadecimal\-digit*  
  
 *hexadecimal\-escape\-sequence hexadecimal\-digit*  
  
## 请参阅  
 [C 常量](../c-language/c-constants.md)