---
title: "控制台和端口 I/O | Microsoft Docs"
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
  - "I/O [CRT], 控制台"
  - "I/O [CRT], 端口"
  - "I/O 例程, 控制台和端口 I/O"
  - "端口, I/O 例程"
  - "例程"
  - "例程, 控制台和端口 I/O"
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 控制台和端口 I/O
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些例程读写在控制台上或指定端口。  控制台 I\/O 例程与流 I\/O 或底层 I\/O 库类型程序兼容。  在执行 I\/O之前，不必打开控制台或端口或关闭，因此此类别中打开或关闭的例程。  在 Windows 操作系统中，这些函数的输出始终处理到控制台，不能重定向。  
  
### 控制台和端口 I\/O例程。  
  
|例程|使用|  
|--------|--------|  
|[\_cgets, \_cgetws](../c-runtime-library/cgets-cgetws.md), [\_cgets\_s、\_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)。|从控制台读取字符串|  
|[\_cprintf，\_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)，[\_cprintf\_s、\_cprintf\_s\_l、\_cwprintf\_s、\_cwprintf\_s\_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|将格式化的数据写入控制台。|  
|[\_cputs](../c-runtime-library/reference/cputs-cputws.md)|把字符串写入控制台|  
|[\_cscanf，\_cwscanf](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)，[\_cscanf\_s、\_cscanf\_s\_l、\_cwscanf\_s、\_cwscanf\_s\_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|从控制台读取格式化的数据|  
|[\_getch、\_getwch](../c-runtime-library/reference/getch-getwch.md)|从控制台读取字符|  
|[\_getche、\_getwche](../c-runtime-library/reference/getch-getwch.md)|从控制台读取字符以及回显它|  
|[\_inp](../c-runtime-library/inp-inpw-inpd.md)|从指定的I\/O端口读取一个字节|  
|[\_inpd](../c-runtime-library/inp-inpw-inpd.md)|从指定 I\/O 端口读取双字|  
|[\_inpw](../c-runtime-library/inp-inpw-inpd.md)|读取指定 I\/O 端口 2 字节的单词|  
|[\_kbhit](../c-runtime-library/reference/kbhit.md)|在控制台检查键击；在尝试从控制台读取使用|  
|[\_outp](../c-runtime-library/outp-outpw-outpd.md)|写入字节到指定 I\/O 端口|  
|[\_outpd](../c-runtime-library/outp-outpw-outpd.md)|对指定的 I\/O 端口的写双字|  
|[\_outpw](../c-runtime-library/outp-outpw-outpd.md)|对指定的 I\/O 端口的写字节|  
|[\_putch、\_putwch](../c-runtime-library/reference/putch-putwch.md)|向控制台写入字符|  
|[\_ungetch，\_ungetwch](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|“Unget”是从控制台读取的最后一个字符，所以它是下一个要被读取的字符。|  
  
## 请参阅  
 [输入和输出](../c-runtime-library/input-and-output.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)