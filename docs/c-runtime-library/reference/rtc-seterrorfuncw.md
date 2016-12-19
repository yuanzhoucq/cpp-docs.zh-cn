---
title: "_RTC_SetErrorFuncW | Microsoft Docs"
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
  - "_RTC_SetErrorFuncW"
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
  - "_RTC_SetErrorFuncW"
  - "RTC_SetErrorFuncW"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "运行时错误"
  - "RTC_SetErrorFuncW 函数"
  - "_RTC_error_fnW typedef"
  - "_RTC_SetErrorFuncW 函数"
  - "RTC_error_fnW typedef"
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _RTC_SetErrorFuncW
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将函数指定为报告运行时错误检查 \(RTC\) 的处理程序。  
  
## 语法  
  
```  
  
_RTC_error_fnW _RTC_SetErrorFuncW(  
   _RTC_error_fnW  
 function   
);  
  
```  
  
#### 参数  
 `function`  
 处理运行时错误检查的函数的地址。  
  
## 返回值  
 为以前定义的错误函数；或者，如果不存在以前定义的任何函数，则为 `NULL`。  
  
## 备注  
 在新代码中，仅使用 `_RTC_SetErrorFuncW`。`_RTC_SetErrorFunc` 仅包含在适用于后向兼容性的库中。  
  
 `_RTC_SetErrorFuncW` 回调仅适用于它链接的组件，但不是全局适用。  
  
 确保传递给 `_RTC_SetErrorFuncW` 的地址是有效的错误处理函数的地址。  
  
 如果已使用 [\_RTC\_SetErrorType](../../c-runtime-library/reference/rtc-seterrortype.md) 给错误分配 –1 类型，则不会调用错误处理函数。  
  
 在可以调用此函数之前，首先必须调用其中一个运行时错误检查初始化函数。 有关更多信息，请参见[使用无 C 运行库的运行时检查](../Topic/Using%20Run-Time%20Checks%20Without%20the%20C%20Run-Time%20Library.md)。  
  
 **\_RTC\_error\_fnW** 定义如下：  
  
 **typedef int \(\_\_cdecl \*\_RTC\_error\_fnW\)\(int**  `errorType` **, const wchar\_t \*** *filename* **, int**  *linenumber* **, const wchar\_t \*** `moduleName` **, const wchar\_t \*** *format* **, ...\);**  
  
 其中：  
  
 `errorType`  
 由 [\_RTC\_SetErrorType](../../c-runtime-library/reference/rtc-seterrortype.md) 指定的错误类型。  
  
 *filename*  
 为发生故障的源文件，或者，如果没有调试信息，则为 null。  
  
 *linenumber*  
 为其中发生故障的 *filename* 中的行，或者，如果没有调试信息，则为 0。  
  
 `moduleName`  
 DLL 或发生故障的可执行文件的名称。  
  
 *format*  
 要使用剩余的参数显示错误消息的 printf 样式字符串。 VA\_ARGLIST 的第一个参数是出现的 RTC 错误号。  
  
 有关演示如何使用 **\_RTC\_error\_fnW** 的示例，请参阅 [本机运行时检查自定义](../Topic/Native%20Run-Time%20Checks%20Customization.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_RTC_SetErrorFuncW`|\<rtcapi.h\>|  
  
 有关更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅 [平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_CrtDbgReport、\_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)   
 [运行时错误检查](../../c-runtime-library/run-time-error-checking.md)