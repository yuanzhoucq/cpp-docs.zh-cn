---
title: _ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l
ms.date: 11/04/2016
apiname:
- _ismbclegal_l
- _ismbclegal
- _ismbcsymbol
- _ismbcsymbol_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ismbcsymbol_l
- _ismbcsymbol_l
- _ismbcsymbol
- _ismbclegal_l
- _ismbclegal
- ismbclegal_l
- ismbcsymbol
- ismbclegal
helpviewer_keywords:
- ismbcsymbol function
- ismbclegal_l function
- _istlegal_l function
- istlegal function
- _istlegal function
- _ismbcsymbol function
- _ismbclegal_l function
- ismbclegal function
- ismbcsymbol_l function
- _ismbclegal function
- _ismbcsymbol_l function
- istlegal_l function
ms.assetid: 31bf1ea5-b56f-4e28-b21e-b49a2cf93ffc
ms.openlocfilehash: 07855ec970b2bf307238982987912f1e91505e96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454569"
---
# <a name="ismbclegal-ismbclegall-ismbcsymbol-ismbcsymboll"></a>_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l

检查多字节字符是合法字符还是符号字符。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _ismbclegal(
   unsigned int c
);
int _ismbclegal_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcsymbol(
   unsigned int c
);
int _ismbcsymbol_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*c*<br/>
要测试的字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

其中每个例程在字符满足测试条件时返回一个非零值，在不满足测试条件时回 0。 如果*c*< = 255 且存在相应 **_ismbb**例程 (例如， **_ismbcalnum**对应于 **_ismbbalnum**)，则结果是相应的返回值 **_ismbb**例程。

## <a name="remarks"></a>备注

其中每个函数都针对给定的条件测试给定的多字节字符。

使用这些函数的版本 **_l**后缀完全相同，只不过它们使用为其区域设置相关的行为而不是当前区域设置传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

|例程所返回的值|测试条件|代码页 932 示例|
|-------------|--------------------|---------------------------|
|**_ismbclegal**|有效多字节|返回非零值，当且仅当第一个字节*c*在范围内 0x81-0x9F 或 0xE0-0xFC，而第二个字节在 0x40-0x7E 或 0x80-FC。|
|**_ismbcsymbol**|多字节字符|返回非零值，当且仅当 0x8141< < =*c*< = 0x81AC。|

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlegal**|始终返回 false|**_ismbclegal**|始终返回 false。|
|**_istlegal_l**|始终返回 false|**_ismbclegal_l**|始终返回 false。|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_ismbclegal**， **_ismbclegal_l**|\<mbstring.h>|
|**_ismbcsymbol**， **_ismbcsymbol_l**|\<mbstring.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[_ismbc 例程](../../c-runtime-library/ismbc-routines.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
