---
title: "stdin、stdout、stderr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdin"
  - "stderr"
  - "stdout"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "标准错误流"
  - "标准输入流"
  - "标准输出流"
  - "stderr 函数"
  - "stdin 函数"
  - "stdout 函数"
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# stdin、stdout、stderr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
      FILE *stdin;   
FILE *stdout;   
FILE *stderr;   
#include <stdio.h>  
```  
  
## 备注  
 以下是输入、输出和错误输出流的标准。  
  
 默认情况下，标准输入从键盘读取，而标准输出和错误输出到屏幕。  
  
 下面流指针可用访问标准流：  
  
|指针|流|  
|--------|-------|  
|`stdin`|标准输入|  
|**stdout**|标准输出|  
|`stderr`|标准错误|  
  
 这些指针可用作指向函数的参数。  某些函数如 **getchar** 和 `putchar`时，自动使用 `stdin` 和 **stdout**。  
  
 这些指针是常数，不能指派新的值。  `freopen` 函数可用于重定向流到磁盘文件或其他设备。  操作系统可以重定向程序进行标准输入和输出在指令水平。  
  
## 请参阅  
 [流 I\/O](../c-runtime-library/stream-i-o.md)   
 [全局常量](../c-runtime-library/global-constants.md)