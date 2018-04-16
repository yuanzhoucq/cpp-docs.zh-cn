---
title: "_RTC_SetErrorType | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f6aaeaabe07f84a10167057ff94b45f91af0c93
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="rtcseterrortype"></a>_RTC_SetErrorType
将运行时错误检查 (RTC) 检测到的错误与类型关联。 错误处理程序处理如何输出指定类型的错误。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int _RTC_SetErrorType(  
   _RTC_ErrorNumber errnum,  
   int ErrType   
);  
```  
  
#### <a name="parameters"></a>参数  
 *errnum*  
 一个数字，介于 0 和 [_RTC_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md)返回的值减 1 所得的值之间。  
  
 *ErrType*  
 要分配给此 *errnum*的值。 例如，可以使用 **_CRT_ERROR**。 如果用 `_CrtDbgReport` 作为错误处理程序， *ErrType* 只能是 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md)中定义的其中一个符号。 如果你有自己的错误处理程序 ([_RTC_SetErrorFunc](../../c-runtime-library/reference/rtc-seterrorfunc.md))，那么你可以拥有与 *errnum*的数量一样多的 *ErrType*。  
  
 _RTC_ERRTYPE_IGNORE 的 *ErrType* 对 `_CrtSetReportMode`具有特殊含义；忽略该错误。  
  
## <a name="return-value"></a>返回值  
 错误类型 `type`的上一个值。  
  
## <a name="remarks"></a>备注  
 默认情况下，所有错误都设置为 *ErrType* = 1，这与 **_CRT_ERROR**对应。 有关默认的错误类型（例如 **_CRT_ERROR**）的详细信息，请参阅 [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)。  
  
 在可以调用此函数之前，首先必须调用其中一个运行时错误检查初始化函数；请参阅[使用无 C 运行时库的运行时检查](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_RTC_SetErrorType`|\<rtcapi.h>|  
  
 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="see-also"></a>请参阅  
 [_RTC_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [运行时错误检查](../../c-runtime-library/run-time-error-checking.md)