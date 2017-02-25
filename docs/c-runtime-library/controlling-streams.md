---
title: "控制流 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Controlling Streams"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制流"
  - "流"
  - "流, 控制"
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 控制流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[fopen](../c-runtime-library/reference/fopen-wfopen.md) 类型返回 `FILE`对象的地址。  使用此地址作为 `stream` 参数。多种库函数执行在打开文件进行各种运算。  对于 Word，限制所有输入发生，就像每个字符调用 [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md)读取，并且，所有输出发生，就像每个字符调用 [fputc](../c-runtime-library/reference/fputc-fputwc.md)编写。  对于 Word，限制所有输入发生，就像每个字符调用 [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)读取，并且，所有输出发生，就像每个字符调用 [fputwc](../c-runtime-library/reference/fputc-fputwc.md)编写。  
  
 您可以通过 [fclose](../c-runtime-library/reference/fclose-fcloseall.md)调用关闭文件，之后，`FILE` 对象的地址无效。  
  
 `FILE` 对象存储在流的状态，包括：  
  
-   的错误指示器集合按非零遇到读取或写入错误的函数。  
  
-   文件尾指示符集合非零。遇到文件的末尾，则读取时的函数。  
  
-   文件，则可以支持位置请求，文件位置指示器在流指定下计算读取或写入。  
  
-   [流状态](../c-runtime-library/stream-states.md) 指定流是否将接受读取和\/或编写，然后流是否未绑定，面向字节的宽或中。  
  
-   转换状态记住任何部分程序集中的或生成的通用字符多的状态，以及字节序列的所有 Shift 状态文件中的\)。  
  
-   文件缓冲区指定库函数中使用以提高性能读取和写入操作。流数组对象的地址和大小。  
  
 请勿修改以指定用于与该对象的文件存储缓冲区中的 `FILE` 对象或任何值。  不能复制一个 `FILE` 对象和 portably 使用复制的地址作为 `stream` 参数对库函数。  
  
## 请参阅  
 [文件和流](../c-runtime-library/files-and-streams.md)