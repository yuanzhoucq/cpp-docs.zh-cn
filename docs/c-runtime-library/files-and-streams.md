---
title: "文件和流 | Microsoft Docs"
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
  - "文件 [C++]"
  - "流"
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 文件和流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

程序与目标环境通信通过读取和写入文件。  文件可以是：  
  
-   可以重复读取和写入的数据集。  
  
-   程序生成的流 \(如字节管线\)。  
  
-   接收或发送给一组设备外围的字节流。  
  
 前两项是交互式的文件。  文件是通常与应用程序交互的主要方法。  操作所有这些文件的方法与通过调用库函数极为相似。  这些函数的声明包含在大多数标准头 STDIO.H 。  
  
 在能够运行许多文件的操作之前，必须打开文件。  打开文件放在该标准的 C 库中将它与流，数据结构在许多差异的它们在中的各种文件。  在文件类型对象中，库维护每个流的状态。  
  
 在程序启动之前，目标环境打开三个文件。  通过调用具有两参数的库函数打开文件[fopen、\_wfopen](../c-runtime-library/reference/fopen-wfopen.md)（`fopen` 函数已弃用，请使用 [fopen\_s、\_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)。\)第一个参数是文件名。  第二个参数为指定的 C 字符串：  
  
-   这是您是要读取文件或数据写入或两个都要的地方。  
  
-   是否生成文件的新内容 \(或创建文件，则以前不存在\) 或者保持现有内容发生。  
  
-   是否对文件的进行编写将修改现有的内容，或只应将字节追加置于文件尾。  
  
-   您是否要操作文本流或文件流。  
  
 一旦成功打开文件，然后定位的流是否面向字节的 \(字节流\) 或面向宽度的 \(宽流\)。  流开始断开。  调用特定函数操作流使其面向字节的，而当其他函数时使其面向宽的。  一旦建立，流维护其方向，直到它调用 [fclose](../c-runtime-library/reference/fclose-fcloseall.md) 或 [freopen](../c-runtime-library/reference/freopen-wfreopen.md)关闭。  
  
 © 1989\-2001 by P.J.  Plauger and Jim Brodie.  保留所有权利。  
  
## 请参阅  
 [文本和二进制流](../c-runtime-library/text-and-binary-streams.md)   
 [字节和宽流](../c-runtime-library/byte-and-wide-streams.md)   
 [控制流](../c-runtime-library/controlling-streams.md)   
 [流状态](../c-runtime-library/stream-states.md)