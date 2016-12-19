---
title: "翻译模式常量 | Microsoft Docs"
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
  - "_O_BINARY"
  - "_O_TEXT"
  - "_O_RAW"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_O_BINARY 常量"
  - "_O_RAW 常量"
  - "_O_TEXT 常量"
  - "O_BINARY 常量"
  - "O_RAW 常量"
  - "O_TEXT 常量"
  - "翻译常量"
  - "翻译模式（文件 I/O）"
  - "翻译, 常量"
  - "翻译, modes"
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 翻译模式常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <fcntl.h>  
  
```  
  
## 备注  
 `_O_BINARY` 和 `_O_TEXT` 指示常量确定转换模式的文件 \(`_open` 和 `_sopen`\) 或流转换模式 \(`_setmode`\)。  
  
 允许的值包括：  
  
 `_O_TEXT`  
 在文本（转换）模式下打开文件。  支架返回行信息提要 \(CR\-LF\) 组合在转换输入的一个换行符（LF）。  行信息符将转换为 CR\-LF 组合输出。  此外，CTRL\+Z 被解释为输入的文件结尾字符。  在使用 `fopen` 打开以进行读取\/写入的文件中， 将检查文件末尾的 CTRL\+Z 并将其移除（如果可能）。  因为使用 `fseek` 和 `ftell` 函数在以 CTRL\+Z 结尾的文件中移动时，这可能导致 `fseek` 在文件末尾附近错误运行。  
  
 `_O_BINARY`  
 在二进制文件 \(未转换\) 模式中打开。  上述的转换是禁止的。  
  
 `_O_RAW`  
 与 `_O_BINARY` 相同。  支持提供 C 2.0 兼容。  
  
 有关更多信息，请参见 [文本和二进制文件 I\/O 模式](../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [文件转换](../c-runtime-library/file-translation-constants.md)。  
  
## 请参阅  
 [\_open、\_wopen](../c-runtime-library/reference/open-wopen.md)   
 [\_pipe](../c-runtime-library/reference/pipe.md)   
 [\_sopen、\_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [\_setmode](../c-runtime-library/reference/setmode.md)   
 [全局常量](../c-runtime-library/global-constants.md)