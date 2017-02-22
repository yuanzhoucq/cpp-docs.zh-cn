---
title: "_get_errno | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_errno"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_get_errno"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_get_errno 函数"
  - "errno 全局变量"
  - "get_errno 函数"
ms.assetid: b3fd5ebc-f41b-4314-a2f4-2f2d79d6e740
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _get_errno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取全局误差变量的当前值。  
  
## 语法  
  
```  
errno_t _get_errno(   
   int * pValue   
);  
```  
  
#### 参数  
 \[out\] `pValue`  
 将用整数的指针复制 `errno` 变量的当前值。  
  
## 返回值  
 如果成功，返回零；如果失败，则为错误代码。  如果 `pValue` 为 `NULL`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `EINVAL`。  
  
## 备注  
 在Errno.h 中定义，可能的 `errno` 值。  请参见：[errno 常量](../../c-runtime-library/errno-constants.md)。  
  
## 示例  
  
```  
// crt_get_errno.c  
#include <stdio.h>  
#include <fcntl.h>  
#include <sys/stat.h>  
#include <share.h>  
#include <errno.h>  
  
int main()  
{  
   errno_t err;  
   int pfh;  
   _sopen_s( &pfh, "nonexistent.file", _O_WRONLY, _SH_DENYNO, _S_IWRITE );  
   _get_errno( &err );  
   printf( "errno = %d\n", err );  
   printf( "fyi, ENOENT = %d\n", ENOENT );  
}  
```  
  
  **errno \= 2**  
**fyi，ENOENT \= 2**   
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_get_errno`|\<stdlib.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework Equivalent  
 不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_set\_errno](../../c-runtime-library/reference/set-errno.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)