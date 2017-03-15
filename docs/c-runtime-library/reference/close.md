---
title: "_close | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_close"
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
  - "_close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_close 函数"
  - "close 函数"
  - "文件 [C++], 关闭"
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _close
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

关闭一个文件。  
  
## 语法  
  
```  
int _close(   
   int fd   
);  
```  
  
#### 参数  
 `fd`  
 引用开启文件的描述符。  
  
## 返回值  
 如果文件成功关闭，`_close`返回 0。  返回值 \-1 指示一个错误。  
  
## 备注  
 `_close` 函数关闭与 `fd`关联的文件。  
  
 关闭文件说明符和基础操作系统文件句柄。  因此，如果文件最初使用 Win32 函数 `CreateFile` 打开，并使用 `_open_osfhandle`转换文件说明符，则`CloseHandle` 不是必需的。  
  
 此函数验证其参数。  如果 `fd` 是无效的文件说明符，此函数调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，函数返回\-1，并将`errno`设置为`EBADF`。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_close`|\<io.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见[\_open](../../c-runtime-library/reference/open-wopen.md)示例。  
  
## 请参阅  
 [低级别 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_chsize](../../c-runtime-library/reference/chsize.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_dup、\_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_unlink、\_wunlink](../../c-runtime-library/reference/unlink-wunlink.md)