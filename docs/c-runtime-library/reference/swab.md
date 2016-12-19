---
title: "_swab | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_swab"
  - "stdlib/_swab"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_swab"
  - "stdlib/_swab"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_swab 函数"
  - "字节, 交换"
  - "swab 函数"
  - "交换字节"
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
caps.latest.revision: 18
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _swab
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

交换字节。  
  
## 语法  
  
```  
void _swab(  
   char *src,  
   char *dest,  
   int n   
);  
```  
  
#### 参数  
 `src`  
 复制和交换数据。  
  
 `dest`  
 交换数据的存储位置。  
  
 `n`  
 复制和交换字节数。  
  
## 备注  
 如果 `n` 值为偶数，`_swab` 函数从 `src`复制 `n` 字节，交换每对相邻字节，并将结果存储在 `dest`中。  如果 `n` 为奇数，复制`_swab` ，交换`src`的第一个`n-1` 字节。  `_swab` 通常用于为传输二进制数据到使用不同字节顺序的计算机上做准备。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_swab`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_swab.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";  
char to[] =   "..........................";  
  
int main()  
{  
    printf( "Before: %s\n        %s\n\n", from, to );  
    _swab( from, to, sizeof( from ) );  
    printf( "After:  %s\n        %s\n\n", from, to );  
}  
```  
  
  **前面：BADCFEHGJILKNMPORQTSVUXWZY**  
 **..........................**  
**后面：BADCFEHGJILKNMPORQTSVUXWZY**  
 **ABCDEFGHIJKLMNOPQRSTUVWXYZ**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [缓冲区操作](../../c-runtime-library/buffer-manipulation.md)