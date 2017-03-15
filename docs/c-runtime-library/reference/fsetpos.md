---
title: "fsetpos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fsetpos"
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
  - "fsetpos"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fsetpos 函数"
  - "流, 设置位置指示器"
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# fsetpos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置流位置指示符。  
  
## 语法  
  
```  
int fsetpos(   
   FILE *stream,  
   const fpos_t *pos   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `pos`  
 位置指示器存储。  
  
## 返回值  
 如果成功，`fsetpos`返回 0 。  对于失败，则函数将返回非零值并将 `errno` 设置为以下清单常数之一 \(在 ERRNO.H定义\): `EBADF`，这意味着文件不可访问或 `stream` 指向的对象不是一个有效的文件结构；或 `EINVAL`，表示对于 `stream` 或 `pos` 是无效值传递的。  如果传递的是无效参数，则这些函数调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  
  
 有关这些内容的详细信息以及其他返回代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `fsetpos` 函数为 `stream` 设置的文件位置指示符为 `pos`的值*，* 在对 `fgetpos` 的优先调用来被获取而不是`stream`*。*函数清除文件尾指示符并撤消 [ungetc](../../c-runtime-library/reference/ungetc-ungetwc.md) 的所有在`stream`的效果*.*在调用 `fsetpos`之后，对 `stream` 的下一操作既可以是输入也可以是输出。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fsetpos`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅 [fgetpos](../../c-runtime-library/reference/fgetpos.md) 示例。  
  
## .NET Framework 等效项  
 [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)