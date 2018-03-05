---
title: "流状态 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- streams, states
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0812d0728bfa17bcac80642f1d8545345a0263f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="stream-states"></a>流状态
下图中显示了流的有效状态及状态转换。  
  
 ![流](../c-runtime-library/media/stream.gif "流")  
  
 每个圆圈代表一种稳定的状态。 每一行代表由对流进行的函数调用所导致的转换。 五组函数可以导致状态转换。  
  
 前三个组中的函数在 \<stdio.h> 中声明：  
  
-   字节读取函数 — [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md)、[fgets](../c-runtime-library/reference/fgets-fgetws.md)、[fread](../c-runtime-library/reference/fread.md)、[fscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、[getc](../c-runtime-library/reference/getc-getwc.md)、[getchar](../c-runtime-library/reference/getc-getwc.md)、[gets](../c-runtime-library/gets-getws.md)、[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 和 [ungetc](../c-runtime-library/reference/ungetc-ungetwc.md)  
  
-   字节写入函数 — [fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)、[fputc](../c-runtime-library/reference/fputc-fputwc.md)、[fputs](../c-runtime-library/reference/fputs-fputws.md)、[fwrite](../c-runtime-library/reference/fwrite.md)、[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)、[putc](../c-runtime-library/reference/putc-putwc.md)、[putchar](../c-runtime-library/reference/putc-putwc.md)、[puts](../c-runtime-library/reference/puts-putws.md)、[vfprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) 和 [vprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)  
  
-   位置函数 — [fflush](../c-runtime-library/reference/fflush.md)、[fseek](../c-runtime-library/reference/fseek-fseeki64.md)、[fsetpos](../c-runtime-library/reference/fsetpos.md) 和 [rewind](../c-runtime-library/reference/rewind.md)  
  
 剩余的两个组中的函数在 \<wchar.h> 中声明：  
  
-   宽读取函数 — [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)、[fgetws](../c-runtime-library/reference/fgets-fgetws.md)、[fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、[getwc](../c-runtime-library/reference/getc-getwc.md)、[getwchar](../c-runtime-library/reference/getc-getwc.md)、[ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md) 和 [wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)，  
  
-   宽写入函数 — [fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)、[fputwc](../c-runtime-library/reference/fputc-fputwc.md)、[fputws](../c-runtime-library/reference/fputs-fputws.md)、[putwc](../c-runtime-library/reference/putc-putwc.md), [putwchar](../c-runtime-library/reference/fputc-fputwc.md)、[vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)、[vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md) 和 [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)，  
  
 状态图显示您必须在大多数写入和读取操作之间调用一个位置函数：  
  
-   如果对流进行的最后一次操作是写入，则您无法调用读取函数。  
  
-   如果对流进行的最后一次操作是读取，则您无法调用写入函数，除非该读取操作设置了文件尾指示符。  
  
 最后，状态图显示位置操作始终不会减少可后续进行的有效函数调用的次数。  
  
## <a name="see-also"></a>请参阅  
 [文件和流](../c-runtime-library/files-and-streams.md)