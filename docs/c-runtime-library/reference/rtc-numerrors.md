---
title: "_RTC_NumErrors | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _RTC_NumErrors
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _RTC_NumErrors
- RTC_NumErrors
dev_langs: C++
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0d305575a2dca1df3084ab413b82d445260a6e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="rtcnumerrors"></a>_RTC_NumErrors
返回可由运行时错误检查 (RTC) 检测出的错误总数。 可以将此数字用作 **for** 循环的控件，循环中的每个值都将传递给 [_RTC_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)。  
  
## <a name="syntax"></a>语法  
  
```  
  
int _RTC_NumErrors( void );  
  
```  
  
## <a name="return-value"></a>返回值  
 一个整数，其值表示可以由 Visual C++ 运行时错误检查检测出的错误总数。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_RTC_NumErrors`|\<rtcapi.h>|  
  
 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="see-also"></a>请参阅  
 [_RTC_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [运行时错误检查](../../c-runtime-library/run-time-error-checking.md)