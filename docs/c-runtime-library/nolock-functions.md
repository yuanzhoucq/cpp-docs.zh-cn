---
title: "_nolock 函数 | Microsoft Docs"
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
  - "_nolock 函数"
  - "nolock 函数"
ms.assetid: 7d651d87-38d2-4303-9897-fdb5f7a3e899
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _nolock 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些函数不执行任何锁。  它们提供给需要优化性能的用户。  有关详细信息，请参阅[多线程库性能](../c-runtime-library/multithreaded-libraries-performance.md)。  
  
 仅如果你的程序是单线程或如果有其自己的锁，则使用\_nolock函数。  
  
 [\_fclose\_nolock](../c-runtime-library/reference/fclose-nolock.md)  
  
 [\_fflush\_nolock](../c-runtime-library/reference/fflush-nolock.md)  
  
 [\_fgetc\_nolock、\_fgetwc\_nolock](../c-runtime-library/reference/fgetc-nolock-fgetwc-nolock.md)  
  
 [\_fread\_nolock](../c-runtime-library/reference/fread-nolock.md)  
  
 [\_fseek\_nolock、\_fseeki64\_nolock](../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md)  
  
 [\_ftell\_nolock、\_ftelli64\_nolock](../c-runtime-library/reference/ftell-nolock-ftelli64-nolock.md)  
  
 [\_fwrite\_nolock](../c-runtime-library/reference/fwrite-nolock.md)  
  
 [\_getc\_nolock、\_getwc\_nolock](../c-runtime-library/reference/getc-nolock-getwc-nolock.md)  
  
 [\_getch\_nolock、\_getwch\_nolock](../c-runtime-library/reference/getch-nolock-getwch-nolock.md)  
  
 [\_getchar\_nolock、\_getwchar\_nolock](../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md)  
  
 [\_getche\_nolock、\_getwche\_nolock](../c-runtime-library/reference/getche-nolock-getwche-nolock.md)  
  
 [\_getdcwd\_nolock、\_wgetdcwd\_nolock](../c-runtime-library/reference/getdcwd-nolock-wgetdcwd-nolock.md)  
  
 [\_putc\_nolock、\_putwc\_nolock](../c-runtime-library/reference/putc-nolock-putwc-nolock.md)  
  
 [\_putch\_nolock、\_putwch\_nolock](../c-runtime-library/reference/putch-nolock-putwch-nolock.md)  
  
 [\_putchar\_nolock、\_putwchar\_nolock](../c-runtime-library/reference/putchar-nolock-putwchar-nolock.md)  
  
 [\_ungetc\_nolock、\_ungetwc\_nolock](../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md)  
  
 [\_ungetch\_nolock, \_ungetwch\_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)  
  
## 请参阅  
 [输入和输出](../c-runtime-library/input-and-output.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)