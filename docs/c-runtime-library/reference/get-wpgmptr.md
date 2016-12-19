---
title: "_get_wpgmptr | Microsoft Docs"
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
  - "_get_wpgmptr"
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
  - "get_wpgmptr"
  - "_get_wpgmptr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_wpgmptr 函数"
  - "_wpgmptr 全局变量"
  - "get_wpgmptr 函数"
  - "wpgmptr 全局变量"
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_wpgmptr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取 `_wpgmptr` 全局变量的当前值。  
  
## 语法  
  
```  
errno_t _get_wpgmptr(     wchar_t **pValue  );  
```  
  
#### 参数  
 \[out\] `pValue`  
 指向要填充 `_wpgmptr` 变量当前值的字符串的指针。  
  
## 返回值  
 如果成功，则返回零；如果失败，则返回错误代码。  如果 `pValue` 为 `NULL`，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
## 备注  
 `_wpgmptr` 全局变量以宽字符字符串形式包含通向与该过程关联的可执行文件的完整路径。  有关详细信息，请参阅[\_pgmptr、\_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_wpgmptr`|\<stdlib.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_get\_pgmptr](../../c-runtime-library/reference/get-pgmptr.md)