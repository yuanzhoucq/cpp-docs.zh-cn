---
title: "_RTC_SetErrorType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_RTC_SetErrorType"
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
  - "RTC_SetErrorType"
  - "_RTC_SetErrorType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "运行时错误"
  - "RTC_SetErrorType 函数"
  - "_RTC_SetErrorType 函数"
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _RTC_SetErrorType
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将运行时错误检查 \(RTC\) 检测到的错误与类型关联。 错误处理程序处理如何输出指定类型的错误。  
  
## 语法  
  
```  
  
int _RTC_SetErrorType(  
   _RTC_ErrorNumber  
errnum  
,  
   int  
ErrType   
);  
  
```  
  
#### 参数  
 *errnum*  
 一个数字，介于 0 和 [\_RTC\_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md) 返回的值减 1 所得的值之间。  
  
 *ErrType*  
 要分配给此 *errnum* 的值。 例如，可以使用 **\_CRT\_ERROR**。 如果用 `_CrtDbgReport` 作为错误处理程序，*ErrType* 只能是 [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 中定义的其中一个符号。 如果你有自己的错误处理程序 \([\_RTC\_SetErrorFunc](../../c-runtime-library/reference/rtc-seterrorfunc.md)\)，那么你可以拥有与 *errnum* 的数量一样多的 *ErrType*。  
  
 \_RTC\_ERRTYPE\_IGNORE 的 *ErrType* 对 `_CrtSetReportMode` 具有特殊含义；忽略该错误。  
  
## 返回值  
 错误类型 `type` 的上一个值。  
  
## 备注  
 默认情况下，所有错误都设置为 *ErrType* \= 1，这与 **\_CRT\_ERROR** 对应。 有关默认的错误类型（例如 **\_CRT\_ERROR**）的详细信息，请参阅 [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)。  
  
 在可以调用此函数之前，首先必须调用其中一个运行时错误检查初始化函数；请参阅[使用无 C 运行时库的运行时检查](../Topic/Using%20Run-Time%20Checks%20Without%20the%20C%20Run-Time%20Library.md)  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_RTC_SetErrorType`|\<rtcapi.h\>|  
  
 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_RTC\_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [运行时错误检查](../../c-runtime-library/run-time-error-checking.md)