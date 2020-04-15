---
title: isspace、iswspace、_isspace_l、_iswspace_l
ms.date: 4/2/2020
api_name:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
- _o_isspace
- _o_iswspace
api_location:
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswspace
- _istspace
- isspace
helpviewer_keywords:
- iswspace function
- isspace function
- _iswspace_l function
- _isspace_l function
- iswspace_l function
- isspace_l function
- _istspace function
- istspace function
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
ms.openlocfilehash: 43d66a191427e886941fd3dcac5dc6b71146b68a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342752"
---
# <a name="isspace-iswspace-_isspace_l-_iswspace_l"></a>isspace、iswspace、_isspace_l、_iswspace_l

确定整数是否表示空格字符。

## <a name="syntax"></a>语法

```C
int isspace(
   int c
);
int iswspace(
   wint_t c
);
int _isspace_l(
   int c,
   _locale_t locale
);
int _iswspace_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*C*<br/>
要测试的整数。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果*c*是空格字符的特定表示形式，则每个例程都返回非零。 如果*c*是空格字符（0x09 - 0x0D 或 0x20），**则 isspace**返回非零值。 **isspace**函数的测试条件的结果取决于区域设置**LC_CTYPE**类别设置;有关详细信息[，请参阅集本地设置_wsetlocale。](setlocale-wsetlocale.md) 这些函数的版本没有 **_l**后缀，因此使用当前区域设置执行任何与区域设置相关的行为;具有 **_l**后缀的版本是相同的，只是它们使用传入区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*c*是对应于标准空白字符的宽字符，**则 iswspace**返回非零值。

如果*c*不是 EOF 或范围 0 到 0xFF（包括）时，**则空间**和 **_isspace_l**的行为未定义。 当使用调试 CRT 库，*并且 c*不是这些值之一时，这些函数将引发断言。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**•** **分空间**|**正空间**|[_ismbcspace](ismbcgraph-functions.md)|**正空间**|

## <a name="remarks"></a>备注

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**正空间**|\<ctype.h>|
|**正空间**|\<ctype.h 1> 或 \<wchar.h 1>|
|**_isspace_l**|\<ctype.h>|
|**_iswspace_l**|\<ctype.h 1> 或 \<wchar.h 1>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
