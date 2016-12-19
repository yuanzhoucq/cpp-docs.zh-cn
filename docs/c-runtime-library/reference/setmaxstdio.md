---
title: "_setmaxstdio | Microsoft Docs"
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
  - "_setmaxstdio"
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
  - "setmaxstdio"
  - "_setmaxstdio"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_setmaxstdio 函数"
  - "最大打开文件数"
  - "打开文件, 最大"
  - "setmaxstdio 函数"
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _setmaxstdio
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置同时打开文件的数量最大数目级别的 `stdio`。  
  
## 语法  
  
```  
int _setmaxstdio(  
   int newmax   
);  
```  
  
#### 参数  
 `newmax`  
 设置同时打开文件的数量最大数目级别的 `stdio`。  
  
## 返回值  
 如果成功，则返回 `newmax`；否则返回 。  
  
 如果 `newmax` 小于 `_IOB_ENTRIES` 或更大然后处理的最大数字中的可用操作系统无效参数，处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果执行允许继续，这个函数返回 \-1并设定`errno` 到 `EINVAL` 。  
  
 有关这些内容以及其他错误代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_setmaxstdio` 功能转换可能同时是打开 `stdio` 级别的文件个数的最大值。  
  
 C 运行时现在 I\/O 支持在 Win32 平台的多个打开文件比以前的版本。  2,048 文件可以同时处于打开 [级别的用于 lowio](../../c-runtime-library/low-level-i-o.md) \(即打开并访问通过 `_open`、`_read`，`_write`，依此类推 I\/O 功能系列\)。  512 文件可以同时处于打开 [级别的用于 lowio](../../c-runtime-library/stream-i-o.md) \(即打开并访问通过 `fopen`、`fgetc`，`fputc`，依此类推 I\/O 功能系列\)。  512 打开文件限制在 `stdio` 级别中增加到最大 2,048 通过 `_setmaxstdio` 函数。  
  
 由于 `stdio`级的函数，如 `fopen`，生成函数放在 `lowio` 顶部，最多 2,048 是使用 C 运行库访问同时打开的文件个数的强烈上限。  
  
> [!NOTE]
>  此上限可能是使之超越由特定 Win32 平台和配置支持。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_setmaxstdio`|\<stdio.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见 [\_getmaxstdio](../../c-runtime-library/reference/getmaxstdio.md) 的示例,有关使用 `_setmaxstdio`。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)