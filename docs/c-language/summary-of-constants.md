---
title: "常量摘要 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "常量, C"
ms.assetid: 4158234c-e189-4e25-970f-52a04bc6380a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 常量摘要
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`constant`:  
 *floating\-point\-constant*  
  
 *integer\-constant*  
  
 *enumeration\-constant*  
  
 *character\-constant*  
  
 *floating\-point\-constant*:  
 *fractional\-constant exponent\-part*  opt *floating\-suffix* opt  
  
 *digit\-sequence exponent\-part floating\-suffix*  opt  
  
 *fractional\-constant*:  
 *digit\-sequence*  opt **.***digit\-sequence*  
  
 *digit\-sequence*  **.**  
  
 *exponent\-part*:  
 **e**  *sign*  opt *digit\-sequence*  
  
 **E**  *sign*  opt *digit\-sequence*  
  
 *sign*: 一个  
 **\+ –**  
  
 *digit\-sequence*:  
 *digit*  
  
 *digit\-sequence digit*  
  
 *floating\-suffix*: 一个  
 **f l F L**  
  
 *integer\-constant*:  
 *decimal\-constant integer\-suffix*  opt  
  
 *octal\-constant integer\-suffix*  opt  
  
 *hexadecimal\-constant integer\-suffix*  opt  
  
 *decimal\-constant*:  
 *nonzero\-digit*  
  
 *decimal\-constant digit*  
  
 *octal\-constant*:  
 **0**  
  
 *octal\-constant octal\-digit*  
  
 *hexadecimal\-constant*:  
 **0x**  *hexadecimal\-digit*  
  
 **0X**  *hexadecimal\-digit*  
  
 *hexadecimal\-constant hexadecimal\-digit*  
  
 *nonzero\-digit*: 一个  
 **1 2 3 4 5 6 7 8 9**  
  
 *octal\-digit*: 一个  
 **0 1 2 3 4 5 6 7**  
  
 *hexadecimal\-digit*: 一个  
 **0 1 2 3 4 5 6 7 8 9**  
  
 **a b c d e f**  
  
 **A B C D E F**  
  
 *unsigned\-suffix*: 一个  
 **u U**  
  
 *long\-suffix*: 一个  
 **l L**  
  
 *character\-constant*:  
 **'** *c\-char\-sequence*  
  
 **'L'** *c\-char\-sequence* **'**  
  
 *integer\-suffix*:  
 *unsigned\-suffix long\-suffix*  opt  
  
 *long\-suffix unsigned\-suffix*  opt  
  
 *c\-char\-sequence*:  
 *c\-char*  
  
 *c\-char\-sequence c\-char*  
  
 *c\-char*:  
 除单引号 \('\)、反斜杠 \(**\\**\) 或换行符 *escape\-sequence* 以外的所有源字符集成员  
  
 *escape\-sequence*:  
 *simple\-escape\-sequence*  
  
 *octal\-escape\-sequence*  
  
 *hexadecimal\-escape\-sequence*  
  
 *simple\-escape\-sequence*: 一个  
 **\\a \\b \\f \\n \\r \\t \\v**  
  
 **\\' \\" \\\\ \\?**  
  
 *octal\-escape\-sequence*:  
 **\\** *octal\-digit*  
  
 **\\** *octal\-digit octal\-digit*  
  
 **\\** *octal\-digit octal\-digit octal\-digit*  
  
 *hexadecimal\-escape\-sequence*:  
 **\\x**  *hexadecimal\-digit*  
  
 *hexadecimal\-escape\-sequence hexadecimal\-digit*  
  
## 请参阅  
 [词法语法](../c-language/lexical-grammar.md)