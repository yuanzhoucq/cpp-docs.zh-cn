---
title: "低级别 I/O | Microsoft Docs"
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
  - "文件句柄 [C++]"
  - "文件句柄 [C++], I/O 函数"
  - "I/O [CRT], 函数"
  - "I/O [CRT], 低级别"
  - "低级别 I/O 例程"
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 低级别 I/O
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些函数直接调用操作系统的底层操作， 而不是I\/O流操作。  底层输入和输出调用不会缓存也不会格式化数据。  
  
 使用下列预定义文件说明符，底层例程可以访问在程序启动时打开的标准流。  
  
|流|文件说明符|  
|-------|-----------|  
|`stdin`|0|  
|`stdout`|1|  
|`stderr`|2|  
  
 当发生错误时，底层 I\/O 例程设置 [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)为全局变量。  当使用底层函数时，只要程序需要 STDIO.H 定义的常量，就必须包含 STDIO.H，如文件尾指示符 \(`EOF`\)。  
  
### 底层 I\/O 函数  
  
|功能|使用|  
|--------|--------|  
|[\_close](../c-runtime-library/reference/close.md)|关闭文件|  
|[\_commit](../c-runtime-library/reference/commit.md)|刷新文件到磁盘|  
|[\_creat、\_wcreat](../c-runtime-library/reference/creat-wcreat.md)|创建文件|  
|[\_dup](../c-runtime-library/reference/dup-dup2.md)|返回给定文件中下一个可用的文件说明符|  
|[\_dup2](../c-runtime-library/reference/dup-dup2.md)|创建特定文件的第二描述符|  
|[\_eof](../c-runtime-library/reference/eof.md)|测试文件结尾|  
|[\_lseek、\_lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|重新定位文件指针到特定位置|  
|[\_open、\_wopen](../c-runtime-library/reference/open-wopen.md)|打开文件|  
|[\_read](../c-runtime-library/reference/read.md)|从文件中读取数据|  
|[\_sopen, \_wsopen](../c-runtime-library/reference/sopen-wsopen.md), [\_sopen\_s、\_wsopen\_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|为文件共享打开文件|  
|[\_tell、\_telli64](../c-runtime-library/reference/tell-telli64.md)|捕获当前文件指针的位置|  
|[\_umask](../c-runtime-library/reference/umask.md), [\_umask\_s](../c-runtime-library/reference/umask-s.md)|设置文件权限掩码|  
|[\_write](../c-runtime-library/reference/write.md)|写数据到文件|  
  
 `_dup` 和 `_dup2` 通常用于将预定义文件说明符关联到不同的文件。  
  
## 请参阅  
 [输入和输出](../c-runtime-library/input-and-output.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [系统调用](../c-runtime-library/system-calls.md)