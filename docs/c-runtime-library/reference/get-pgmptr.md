---
title: "_get_pgmptr | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_pgmptr"
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
  - "get_pgmptr"
  - "_get_pgmptr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_pgmptr 函数"
  - "_pgmptr 全局变量"
  - "get_pgmptr 函数"
  - "pgmptr 全局变量"
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_pgmptr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取`_pgmptr`全局误差变量的当前值。  
  
## 语法  
  
```  
errno_t _get_pgmptr(   
   char **pValue   
);  
```  
  
#### 参数  
 \[out\] `pValue`  
 用的字符串的指针填充当前 `_pgmptr` 变量的值。  
  
## 返回值  
 如果成功，返回零；如果失败，则为错误代码。  如果 `pValue` 为 `NULL`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `EINVAL`。  
  
## 备注  
 全局 `_pgmptr`变量包含完整路径。可执行的与进程。  有关详细信息，请参阅[\_pgmptr、\_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_pgmptr`|\<stdlib.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework Equivalent  
 不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_get\_wpgmptr](../../c-runtime-library/reference/get-wpgmptr.md)