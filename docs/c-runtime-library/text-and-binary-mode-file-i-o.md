---
title: "文本和二进制模式文件 I/O | Microsoft Docs"
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
  - "c.io"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "二进制访问"
  - "二进制访问, 二进制模式文件 I/O"
  - "文件 [C++], 打开函数"
  - "函数 [CRT], 文件访问"
  - "I/O [CRT], binary"
  - "I/O [CRT], 文本文件"
  - "I/O [CRT], 翻译模式"
  - "文本文件, I/O"
  - "翻译模式（文件 I/O）"
  - "翻译, modes"
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 文本和二进制模式文件 I/O
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文件 I\/O 操作代替这两种变换模式，文本，或二进制，具体取决于文件打开的模式。  数据文件都通常按文本模式处理。  若要控制文件转换模式，一种可以：  
  
-   打开选定的文件时，请保留当前默认设置并指定该替代模式。  
  
-   使用函数 [\_set\_fmode](../c-runtime-library/reference/set-fmode.md) 更改新打开文件的默认模式。  使用 [\_get\_fmode](../c-runtime-library/reference/get-fmode.md) 查找当前默认模式。  初始默认设置为文本模式 \(`_O_TEXT`\)。  
  
-   通过在程序中设置全局变量[\_fmode](../c-runtime-library/fmode.md)，直接更改默认转换模式。  函数 `_set_fmode` 设置此变量值，也可以直接设置。  
  
 当调用一打开文件函数，如 [\_open](../c-runtime-library/reference/open-wopen.md)、[fopen](../c-runtime-library/reference/fopen-wfopen.md)、[fopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)、[freopen](../c-runtime-library/reference/freopen-wfreopen.md)、[freopen\_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)、[\_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 或 [\_sopen\_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)时，可通过指定函数 [\_set\_fmode](../c-runtime-library/reference/set-fmode.md)相应的参数来重写 `_fmode` 的当前默认设置。  `stdin`、`stdout`和 `stderr`流默认以文本模式打开；在打开任何一个这些文件时，也可以重写该默认值。  打开文件后，使用 [\_setmode](../c-runtime-library/reference/setmode.md) 使用文件说明符更改转换模式。  
  
## 请参阅  
 [输入和输出](../c-runtime-library/input-and-output.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)