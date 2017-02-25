---
title: "文本和二进制模式下的 Unicode 流 I/O | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.io"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "I/O [CRT], unicode 流"
  - "流 I/O 例程"
  - "Unicode 流 I/O"
  - "Unicode, 流 I/O 例程"
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 文本和二进制模式下的 Unicode 流 I/O
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Unicode 流 I\/O 例程 \(例如 `fwprintf`、`fwscanf`、`fgetwc`、`fputwc`、`fgetws`或 `fputws`\) 在以文本模式打开下操作文件 \(默认值\) ，两种字符转换发生：  
  
-   Unicode 对 MBCS 或 MBCS 对 Unicode 转换。  当 Unicode 流 I\/O 函数在文本模式下运行时，源或目标流将假定为一系列多字节字符。  因此，Unicode 流输入函数将多字节字符转换为宽字符（就像调用 `mbtowc` 函数一样）。  出于同一原因，Unicode 流输出函数将宽字符转换为多字节字符（就像调用 `wctomb` 函数一样）。  
  
-   回车符\-换行符 \(CR\-LF\) 转换。  此转换在 MBCS 对 Unicode 转换之前发生 \(Unicode 流输入函数\) 和在 Unicode 对 MBCS转换后发生\(Unicode 输出流函数\)。  在输入过程中，每一个回车 \- 换行组合被翻译成一个换行符。  在输出时，每一个换行字符转换为一个回车 \- 换行组合。  
  
 然而，当一个Unicode I \/ O 流函数以二进制模式操作，该文件被认为是Unicode，并且在输入或输出过程中不会发生CR\-LF翻译或字符转换。  使用 \_setmode \(\_fileno \(stdin\)，\_O\_BINARY\)；指令是为了正确使用 UNICODE 文本文件的 wcin。  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [输入和输出](../c-runtime-library/input-and-output.md)