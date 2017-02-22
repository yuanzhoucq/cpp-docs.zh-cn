---
title: "_set_errno | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_errno"
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
  - "set_errno"
  - "_set_errno"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_errno 函数"
  - "errno 全局变量"
  - "set_errno 函数"
ms.assetid: d338914a-1894-4cf3-ae45-f2c4eb26590b
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _set_errno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将 `errno` 全局变量的值。  
  
## 语法  
  
```  
errno_t _set_errno(   
   int value   
);  
```  
  
#### 参数  
 \[in\] `value`  
 `errno` 的新值。  
  
## 返回值  
 如果成功则返回 0。  
  
## 备注  
 可能的值在Errno.h 中定义。  请参见：[errno 常量](../../c-runtime-library/errno-constants.md)。  
  
## 示例  
  
```  
// crt_set_errno.c  
#include <stdio.h>  
#include <errno.h>  
  
int main()  
{  
   _set_errno( EILSEQ );  
   perror( "Oops" );  
}  
```  
  
  **Oops：非法字节序列**   
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_set_errno`|\<stdlib.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [\_get\_errno](../../c-runtime-library/reference/get-errno.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)