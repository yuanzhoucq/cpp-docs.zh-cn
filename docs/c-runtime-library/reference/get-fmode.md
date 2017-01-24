---
title: "_get_fmode | Microsoft Docs"
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
  - "_get_fmode"
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
  - "get_fmode"
  - "_get_fmode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_fmode 函数"
  - "文件翻译 [C++], 默认模式"
  - "get_fmode 函数"
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_fmode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取文件 I\/O 操作的默认文件翻译模式。  
  
## 语法  
  
```  
errno_t _get_fmode(   
   int * pmode   
);  
```  
  
#### 参数  
 \[out\] `pmode`  
 要填充的整数指针当前默认模式：`_O_TEXT` 或 `_O_BINARY`。  
  
## 返回值  
 如果成功，返回零；如果失败，则为错误代码。  如果 `pmode` 为 `NULL`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`EINVAL`。  
  
## 备注  
 函数获取 [\_fmode](../../c-runtime-library/fmode.md)全局变量的值。  此变量为低指定特定模式的默认文件和流文件 I\/O 操作，如 `_open`、`_pipe`、`fopen`和 `freopen`。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_get_fmode`|\<stdlib.h\>|\<fcntl.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 参见 [\_set\_fmode](../../c-runtime-library/reference/set-fmode.md)的示例。  
  
## .NET Framework Equivalent  
 不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_fmode](../../c-runtime-library/fmode.md)   
 [\_set\_fmode](../../c-runtime-library/reference/set-fmode.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)   
 [文本和二进制模式文件 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)