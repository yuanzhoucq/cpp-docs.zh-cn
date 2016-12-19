---
title: "_RTC_NumErrors | Microsoft Docs"
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
  - "_RTC_NumErrors"
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
  - "_RTC_NumErrors"
  - "RTC_NumErrors"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "运行时错误"
  - "_RTC_NumErrors 函数"
  - "RTC_NumErrors 函数"
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _RTC_NumErrors
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回可由运行时错误检查 \(RTC\) 检测出的错误总数。 可以将此数字用作 **for** 循环的控件，循环中的每个值都将传递给 [\_RTC\_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)。  
  
## 语法  
  
```  
  
int _RTC_NumErrors( void );  
  
```  
  
## 返回值  
 一个整数，其值表示可以由 Visual C\+\+ 运行时错误检查检测出的错误总数。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_RTC_NumErrors`|\<rtcapi.h\>|  
  
 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_RTC\_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [运行时错误检查](../../c-runtime-library/run-time-error-checking.md)