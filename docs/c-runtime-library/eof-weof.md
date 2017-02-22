---
title: "EOF、WEOF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EOF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EOF 函数"
  - "WEOF 函数"
  - "文件结尾"
ms.assetid: a7150563-cdae-4cdf-9798-ad509990e505
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# EOF、WEOF
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <stdio.h>  
```  
  
## 备注  
 EOF 由 I\/O 例程将返回，当文件尾或 \(在某些情况下\) 遇到错误。  
  
 WEOF 为返回值为 **wint\_t** 类型的值，用于发出信号的宽流的末尾，也报告错误状态。  
  
## 请参阅  
 [putc、putwc](../c-runtime-library/reference/putc-putwc.md)   
 [ungetc、ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [fflush](../c-runtime-library/reference/fflush.md)   
 [fclose、\_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_ungetch、\_ungetwch、\_ungetch\_nolock、\_ungetwch\_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)   
 [\_putch、\_putwch](../c-runtime-library/reference/putch-putwch.md)   
 [isascii，\_\_isascii、 iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)   
 [全局常量](../c-runtime-library/global-constants.md)