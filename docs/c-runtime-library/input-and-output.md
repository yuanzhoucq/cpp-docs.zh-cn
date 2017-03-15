---
title: "输入和输出 | Microsoft Docs"
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
  - "I/O [CRT]"
  - "I/O [CRT], 例程"
  - "I/O 例程"
  - "输入例程"
  - "输出例程"
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 输入和输出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

I\/O 进出文件和设备函数读取和写入数据。  文件 I\/O 操作。文本模式或二进制模式发生。  Microsoft 运行库有 I\/O 函数的三种类型：  
  
-   [I\/O 流](../c-runtime-library/stream-i-o.md) 函数将作为单个字符的数据流。  
  
-   [Low\-level I\/O](../c-runtime-library/low-level-i-o.md)函数直接调用操作系统的底层操作， 而不是I\/O流操作。  
  
-   [控制台和 I\/O 端口](../c-runtime-library/console-and-port-i-o.md) 函数读取或直接写入控制台 \(键盘和屏幕\) 或 I\/O 端口 \(如端口\) 打印。  
  
    > [!NOTE]
    >  由于当前函数缓存，并且函数不是低级别，这两种函数的类型通常不兼容。  对于处理特定文件，请使用完全流入或低函数。  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)