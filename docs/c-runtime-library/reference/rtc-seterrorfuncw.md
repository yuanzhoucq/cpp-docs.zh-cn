---
title: "_RTC_SetErrorFuncW | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _RTC_SetErrorFuncW
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
- _RTC_SetErrorFuncW
- RTC_SetErrorFuncW
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d71962eca033e5d3994c82e666102f44c62e82be
ms.lasthandoff: 02/24/2017

---
# <a name="rtcseterrorfuncw"></a>_RTC_SetErrorFuncW
将函数指定为报告运行时错误检查 (RTC) 的处理程序。  
  
## <a name="syntax"></a>语法  
  
```  
  
      _RTC_error_fnW _RTC_SetErrorFuncW(  
   _RTC_error_fnW function   
);  
```  
  
#### <a name="parameters"></a>参数  
 `function`  
 处理运行时错误检查的函数的地址。  
  
## <a name="return-value"></a>返回值  
 为以前定义的错误函数；或者，如果不存在以前定义的函数，则为 `NULL`。  
  
## <a name="remarks"></a>备注  
 在新代码中，仅使用 `_RTC_SetErrorFuncW`。 `_RTC_SetErrorFunc` 仅包含在适用于后向兼容性的库中。  
  
 `_RTC_SetErrorFuncW` 回叫仅适用于其链接的组件，但不是全局适用。  
  
 确保传递给 `_RTC_SetErrorFuncW` 的地址是有效的错误处理函数的地址。  
  
 如果已使用 [_RTC_SetErrorType](../../c-runtime-library/reference/rtc-seterrortype.md) 给错误分配了类型 –1，则不会调用错误处理函数。  
  
 在可以调用此函数之前，首先必须调用其中一个运行时错误检查初始化函数。 有关详细信息，请参阅[使用无 C 运行时库的运行时检查](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)。  
  
 **_RTC_error_fnW** 定义如下：  
  
 **typedef int (__cdecl \*_RTC_error_fnW)(int**  `errorType` **，const wchar_t \*** *filename* **， int**  *linenumber* **，const wchar_t \*** `moduleName` **，const wchar_t \*** *format* ** ，...)；**  
  
 其中：  
  
 `errorType`  
 由 [_RTC_SetErrorType](../../c-runtime-library/reference/rtc-seterrortype.md) 指定的错误类型。  
  
 *filename*  
 为发生故障的源文件，或者，如果没有调试信息，则为 null。  
  
 *linenumber*  
 *filename* 中出现故障的行，如果没有调试信息，则为 0。  
  
 `moduleName`  
 DLL 或发生故障的可执行文件的名称。  
  
 *格式*  
 要使用剩余的参数显示错误消息的 printf 样式字符串。 VA_ARGLIST 的第一个自变量是出现的 RTC 错误号。  
  
 有关演示如何使用 **_RTC_error_fnW** 的示例，请参阅[本机运行时检查自定义](/visualstudio/debugger/native-run-time-checks-customization)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_RTC_SetErrorFuncW`|\<rtcapi.h>|  
  
 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [_CrtDbgReport、_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)   
 [运行时错误检查](../../c-runtime-library/run-time-error-checking.md)
