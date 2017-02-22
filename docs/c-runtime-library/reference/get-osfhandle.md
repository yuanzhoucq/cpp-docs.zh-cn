---
title: "_get_osfhandle | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_osfhandle"
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
  - "get_osfhandle"
  - "_get_osfhandle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "操作系统, 获取文件句柄"
  - "get_osfhandle 函数"
  - "_get_osfhandle 函数"
  - "文件句柄 [C++], 操作系统"
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _get_osfhandle
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索与已指定的文件说明符的操作系统句柄的文件。  
  
## 语法  
  
```  
intptr_t _get_osfhandle(   
   int fd   
);  
```  
  
#### 参数  
 `fd`  
 现有文件说明符。  
  
## 返回值  
 操作系统句柄的文件 `fd`，则有效。  如果 [参数验证](../../c-runtime-library/parameter-validation.md) 为 NULL，则将调用无效参数处理程序，如所述。  如果允许继续执行，则该函数返回 `INVALID_HANDLE_VALUE` \(\- 1\) 并将 `errno` 设置为 `EBADF`，则指示无效的文件句柄。  
  
## 备注  
 关闭`_get_osfhandle`打开的文件，调用 `_close`。  调用`_close`也关闭基础句柄，因此，调用原始句柄的 Win32 函数 `CloseHandle` 是不必要的。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_osfhandle`|\<io.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_dup、\_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)