---
title: _ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l
ms.date: 11/04/2016
apiname:
- _ismbstrail
- _ismbslead_l
- _ismbslead
- _ismbstrail_l
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
- _ismbslead
- ismbs
- ismbslead_l
- _ismbs
- ismbstrail_l
- ismbslead
- _ismbstrail
- _ismbstrail_l
- ismbstrail
- _ismbslead_l
helpviewer_keywords:
- ismbstrail function
- _ismbslead function
- ismbslead function
- ismbslead_l function
- _ismbstrail function
- _ismbslead_l function
- ismbstrail_l function
- _ismbstrail_l function
ms.assetid: 86d2cd7a-3cff-443a-b713-14cc17a231e9
ms.openlocfilehash: 5b4d3f371f4be640cc22a1bdc3d920acf88e2585
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468908"
---
# <a name="ismbslead-ismbstrail-ismbsleadl-ismbstraill"></a>_ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l

对多字节字符串前导字节和结尾字节执行上下文相关测试，并确定给定子字符串指针指向前导字节还是结尾字节。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _ismbslead(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbstrail(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbslead_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
int _ismbstrail_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*str*<br/>
指向字符串开头或之前已知的前导字节的指针。

*current*<br/>
指向要测试的字符串中位置的指针。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_ismbslead**如果字符是前导字节，则返回-1 并 **_ismbstrail**如果字符为结尾字节，则返回-1。 如果输入字符串有效，但不是前导字节也不是结尾字节，则这些函数将返回零。 如果任一参数为**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，这些函数将返回**NULL**并设置**errno**到**EINVAL**。

## <a name="remarks"></a>备注

**_ismbslead**并 **_ismbstrail**比 **_ismbblead**并 **_ismbbtrail**版本因为将字符串文本考虑进去。

具有这些函数的版本 **_l**后缀完全相同，只不过它们可以为其区域设置相关的行为来使用而不是当前区域设置中传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_ismbslead**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|
|**_ismbstrail**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|
|**_ismbslead_l**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|
|**_ismbstrail_l**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|

\* 适用于测试条件的清单常量。

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[_ismbc 例程](../../c-runtime-library/ismbc-routines.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
