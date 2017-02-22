---
title: "_RTC_GetErrDesc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_RTC_GetErrDesc"
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
  - "RTC_GetErrDesc"
  - "_RTC_GetErrDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "运行时错误"
  - "_RTC_GetErrDesc 函数"
  - "RTC_GetErrDesc 函数"
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _RTC_GetErrDesc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回运行时错误检查 \(RTC\) 类型的简要描述。  
  
## 语法  
  
```  
  
const char * _RTC_GetErrDesc(  
   _RTC_ErrorNumber   
errnum  
);  
  
```  
  
#### 参数  
 *errnum*  
 一个数字，介于 0 和 `_RTC_NumErrors` 返回的值减 1 所得的值之间。  
  
## 返回值  
 一个字符串，其中包含由运行时错误检查系统检测到的一个错误类型的简短描述。 如果错误小于 0 或大于等于 [\_RTC\_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md) 返回的值，则 `_RTC_GetErrDesc` 将返回 NULL。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_RTC_GetErrDesc`|\<rtcapi.h\>|  
  
 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [\_RTC\_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md)   
 [运行时错误检查](../../c-runtime-library/run-time-error-checking.md)