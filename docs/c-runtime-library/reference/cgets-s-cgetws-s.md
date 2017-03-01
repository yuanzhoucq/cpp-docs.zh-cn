---
title: "_cgets_s、_cgetws_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cgetws_s
- _cgets_s
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
caps.latest.revision: 31
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.openlocfilehash: 267963b8f9344cef67788726bd2c6f082c7953ac
ms.lasthandoff: 02/24/2017

---
# <a name="cgetss-cgetwss"></a>_cgets_s、_cgetws_s
从控制台获取字符串。 如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述，这些 [_cgets 和 _cgetws](../../c-runtime-library/cgets-cgetws.md) 版本具有安全性增强功能。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _cgets_s(   
   char *buffer,  
   size_t numberOfElements,  
   size_t *pSizeRead  
);  
errno_t _cgetws_s(  
   wchar_t *buffer  
   size_t numberOfElements,  
   size_t *pSizeRead  
);  
template <size_t size>  
errno_t _cgets_s(   
   char (&buffer)[size],  
   size_t *pSizeRead  
); // C++ only  
template <size_t size>  
errno_t _cgetws_s(  
   wchar_t (&buffer)[size],  
   size_t *pSizeRead  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 [out] `buffer`  
 数据的存储位置。  
  
 [in] `numberOfElements`  
 缓冲区的大小（以单字节或宽字符为单位），这也是要读取的最大字符数。  
  
 [in] `pSizeRead`  
 实际读取的字符数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回值为零；否则，如果发生失败，则是错误代码。  
  
### <a name="error-conditions"></a>错误条件  
  
|`buffer`|`numberOfElements`|`pSizeRead`|返回|`buffer` 的内容|  
|--------------|------------------------|-----------------|------------|--------------------------|  
|`NULL`|any|any|`EINVAL`|无|  
|非 `NULL`|零|任何|`EINVAL`|未修改|  
|非 `NULL`|任何|`NULL`|`EINVAL`|零长度字符串|  
  
## <a name="remarks"></a>备注  
 `_cgets_s` 和 `_cgetws_s` 从控制台读取字符串，然后将该字符串（带有 null 结束符）复制到 `buffer`。 `_cgetws_s` 是函数的宽字符版本；除了字符大小之外，这两个函数的行为相同。 要读取的字符串的最大大小作为 `numberOfElements` 参数传入。 此大小应包括用于终止 null 的额外字符。 读取的实际字符数置于 `pSizeRead` 中。  
  
 如果在操作期间或在参数验证中发生错误，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
 在 C++ 中，模板重载简化了这些函数的使用；重载可以自动推断缓冲区长度，从而无需指定大小自变量，并且它们可以自动将较旧、不安全的函数替换为更新、更安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_cgetts_s`|`_cgets_s`|`_cgets_s`|`_cgetws_s`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_cgets_s`|\<conio.h>|  
|`_cgetws_s`|\<conio.h> 或 \<wchar.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [控制台和端口 I/O](../../c-runtime-library/console-and-port-i-o.md)   
 [_getch、_getwch](../../c-runtime-library/reference/getch-getwch.md)
