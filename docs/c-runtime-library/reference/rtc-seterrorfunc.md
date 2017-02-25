---
title: "_RTC_SetErrorFunc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_RTC_SetErrorFunc"
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
apitype: "DLLExport"
f1_keywords: 
  - "RTC_SetErrorFunc"
  - "_RTC_SetErrorFunc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RTC_SetErrorFunc 函数"
  - "_RTC_SetErrorFunc 函数"
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _RTC_SetErrorFunc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将函数指定为报告运行时错误检查 \(RTC\) 的处理程序。 此函数已弃用；请改用 `_RTC_SetErrorFuncW`。  
  
## 语法  
  
```  
  
_RTC_error_fn _RTC_SetErrorFunc(  
   _RTC_error_fn  
 function   
);  
  
```  
  
#### 参数  
 *函数*  
 处理运行时错误检查的函数的地址。  
  
## 返回值  
 以前定义的错误函数。 如果没有以前定义的函数，则返回 NULL。  
  
## 备注  
 请勿使用此函数；请改用 `_RTC_SetErrorFuncW`。 仅为后向兼容性保留使用此函数。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_RTC_SetErrorFunc`|\<rtcapi.h\>|  
  
 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_CrtDbgReport、\_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)   
 [运行时错误检查](../../c-runtime-library/run-time-error-checking.md)