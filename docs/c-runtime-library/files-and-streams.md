---
title: "文件和流 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- files [C++]
- streams
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 42237a142226d70b3cff0c07de5ed3daaeda8682
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="files-and-streams"></a>文件和流
程序通过读取和写入文件来与目标环境进行通信。 文件可以是：  
  
-   可重复读取和写入的数据集。  
  
-   程序生成的字节流（如管线）。  
  
-   从外围设备接收或发送到外围设备的字节流。  
  
 最后两项是交互式文件。 文件通常是用来与程序进行交互的主要手段。 您操作所有此类文件的方式与调用库函数的方式极为相似。 您包括标准标头 STDIO.H 来声明其中的大多数函数。  
  
 必须先打开文件，然后才能对该文件执行许多操作。 打开文件会将其与流、标准 C 库（屏蔽了各种文件之间的许多差异）中的数据结构关联。 库将维护类型 FILE 的对象中的每个流的状态。  
  
 在程序启动前，目标环境将打开三个文件。 可通过将库函数 [fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md) 与两个参数一起调用来打开文件。 （`fopen` 函数已弃用，请改用 [fopen_s、_wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)。）第一个自变量是文件名。 第二个参数是指定以下内容的 C 字符串：  
  
-   您是否想从该文件中读取数据和/或将数据写入该文件中。  
  
-   您是想为文件生成新内容（或创建文件，如果文件之前不存在）还是保留现有内容。  
  
-   对文件进行写入是否可更改现有内容还是只应在文件尾追加字节。  
  
-   您是要操作文本流还是二进制流。  
  
 一旦成功打开此文件，您就可以确定此流是面向字节的（字节流）还是面向宽度的（宽度流）。 最初，流处于未绑定状态。 调用要对流使用的特定函数可使流成为面向字节的流，而其他函数可使流成为面向宽度的流。 在建立流后，它将维护自己的方向，直至通过调用 [fclose](../c-runtime-library/reference/fclose-fcloseall.md) 或 [freopen](../c-runtime-library/reference/freopen-wfreopen.md) 将其关闭。  
  
 © 1989-2001（由 P.J. Plauger 和 Jim Brodie 撰写）。 保留所有权利。  
  
## <a name="see-also"></a>另请参阅  
 [文本和二进制流](../c-runtime-library/text-and-binary-streams.md)   
 [字节和宽流](../c-runtime-library/byte-and-wide-streams.md)   
 [控制流](../c-runtime-library/controlling-streams.md)   
 [流状态](../c-runtime-library/stream-states.md)