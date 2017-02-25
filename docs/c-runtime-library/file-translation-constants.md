---
title: "文件翻译常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.constants.file"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "常量 [C++], 文件翻译模式"
  - "文件翻译 [C++]"
  - "文件翻译 [C++], 常量"
  - "翻译常量"
  - "翻译, 常量"
  - "翻译, 文件翻译常量"
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 文件翻译常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <stdio.h>  
```  
  
## 备注  
 这些常数指定转换模式 \(**"b"** 或 **"t"**\)。  字符串中的模式指定类型访问权限 \(**"r"**、**"w"**、**"a"**、**"r\+"**、**"w\+"**，**"a\+"**\)。  
  
 转换模式如下：  
  
 **t**  
 在文本（转换）模式下打开。  在这模式下，输入时，回车\-换行组合 \(CR\-LF\) 将转换为单一换行组合 \(LF\)，输出时，LF字符将转换为 CR\-LF 组合。  此外，CTRL\+Z 被解释为输入的文件结尾字符。  在为读取或读\/写打开的文件，如果可能，`fopen` 将检查文件末尾的 CTRL\+Z 并将其移除。  因为使用 `fseek` 和 `ftell` 函数在以 CTRL\+Z 结尾的文件中移动时，这可能导致 `fseek` 在文件末尾附近错误运行。  
  
> [!NOTE]
>  **t** 选项不是`fopen` 和 `freopen`的ANSI 标准的部分 。  它是 Microsoft 的扩展，因而不应使用在需要 ANSI 可移植性的地方。  
  
 **b**  
 在二进制 \(未转换\) 模式中打开。  上述的转换是禁止的。  
  
 如果 **t**或 **b** 不在*mode*中，则转换模式由默认模式变量[\_fmode](../c-runtime-library/fmode.md) 定义。  有关使用文本和二进制模式的更多信息，请参见 [文本和二进制 I\/O 模式文件](../c-runtime-library/text-and-binary-mode-file-i-o.md)。  
  
## 请参阅  
 [\_fdopen、\_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen、\_wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、\_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [\_fsopen、\_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [全局常量](../c-runtime-library/global-constants.md)