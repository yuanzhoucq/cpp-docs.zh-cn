---
title: _cgets_s、_cgetws_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
ms.openlocfilehash: 8341b775df3b9cbaececdfaa1f17e075d7c7416c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588534"
---
# <a name="cgetss-cgetwss"></a>_cgets_s、_cgetws_s

从控制台获取字符串。 如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述，这些 [_cgets 和 _cgetws](../../c-runtime-library/cgets-cgetws.md) 版本具有安全性增强功能。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*buffer*<br/>
数据的存储位置。

*numberOfElements*<br/>
缓冲区的大小（以单字节或宽字符为单位），这也是要读取的最大字符数。

*pSizeRead*<br/>
实际读取的字符数。

## <a name="return-value"></a>返回值

如果成功，则返回值为零；否则，如果发生失败，则是错误代码。

### <a name="error-conditions"></a>错误条件

|*buffer*|*numberOfElements*|*pSizeRead*|返回|内容*缓冲区*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**NULL**|任何|任何|**EINVAL**|n/a|
|不**NULL**|零|任何|**EINVAL**|未修改|
|不**NULL**|任何|**NULL**|**EINVAL**|零长度字符串|

## <a name="remarks"></a>备注

**_cgets_s**并 **_cgetws_s**从控制台读取一个字符串，并将字符串 （具有 null 结束符） 复制到*缓冲区*。 **_cgetws_s**是宽字符版本的函数; 除了字符大小，这两个函数的行为是相同。 要读取的字符串的最大大小作为传入*numberOfElements*参数。 此大小应包括用于终止 null 的额外字符。 实际读取的字符数置于*pSizeRead*。

如果在操作期间或在参数验证中发生错误，则调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则**errno**设置为**EINVAL**并**EINVAL**返回。

在 C++ 中，模板重载简化了这些函数的使用；重载可以自动推断缓冲区长度，从而无需指定大小自变量，并且它们可以自动将较旧、不安全的函数替换为更新、更安全的函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_cgets_s**|\<conio.h>|
|**_cgetws_s**|\<conio.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[控制台和端口 I/O](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch、_getwch](getch-getwch.md)<br/>
