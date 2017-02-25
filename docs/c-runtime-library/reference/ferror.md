---
title: "ferror | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ferror"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "ferror"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "错误 [C++], 测试流"
  - "ferror 函数"
  - "流, 测试错误"
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# ferror
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在流中测试错误。  
  
## 语法  
  
```  
int ferror(   
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 如果`stream`没有发生错误，`ferror` 返回 0。  否则，它返回一个非零值。  如果流为 `NULL`，`ferror` 将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回0 。  
  
 有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `ferror` 例程 \(作为函数和宏实现\) 在测试与 `stream`关联的文件读写错误。  如果发生错误，而流的错误指示器保留设置，直到流被关闭或倒带，或者直到`clearerr` 被调用。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`ferror`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [feof](../../c-runtime-library/reference/feof.md) 的示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [错误处理](../../c-runtime-library/error-handling-crt.md)   
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [\_eof](../../c-runtime-library/reference/eof.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [perror、\_wperror](../../c-runtime-library/reference/perror-wperror.md)