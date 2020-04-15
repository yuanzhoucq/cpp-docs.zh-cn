---
title: _ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l
ms.date: 4/2/2020
api_name:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
- _o__ismbclower
- _o__ismbclower_l
- _o__ismbcupper
- _o__ismbcupper_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbcupper
- _ismbclower
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
ms.openlocfilehash: 9a0991d974c33cff22044364f7a4351f160215a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342933"
---
# <a name="_ismbclower-_ismbclower_l-_ismbcupper-_ismbcupper_l"></a>_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l

检查多字节字符是大写还是小写。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _ismbclower(
   unsigned int c
);
int _ismbclower_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcupper(
   unsigned int c
);
int _ismbcupper_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*C*<br/>
要测试的字符。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

其中每个例程在字符满足测试条件时返回一个非零值，在不满足测试条件时回 0。 如果*c*<= 255 并且存在相应的 **_ismbb**例程（例如 **，_ismbcalnum**对应于 **_ismbbalnum），** 则结果是相应的 **_ismbb**例程的返回值。

## <a name="remarks"></a>备注

其中每个函数都针对给定的条件测试给定的多字节字符。

具有 **_l**后缀的这些函数的版本是相同的，只是它们使用传入区域设置，而不是当前区域设置，用于其与区域设置相关的行为。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

|例程|测试条件|代码页 932 示例|
|-------------|--------------------|---------------------------|
|**_ismbclower**|小写字母|仅当*c*是 ASCII 小写英语字母的单字节表示形式：0x61<=*c*<=0x7A 时，才返回非零。|
|**_ismbclower_l**|小写字母|仅当*c*是 ASCII 小写英语字母的单字节表示形式：0x61<=*c*<=0x7A 时，才返回非零。|
|**_ismbcupper**|大写字母|仅当*c*是 ASCII 大写英语字母的单字节表示形式：0x41<=*c*<=0x5A 时，才返回非零。|
|**_ismbcupper_l**|大写字母|仅当*c*是 ASCII 大写英语字母的单字节表示形式：0x41<=*c*<=0x5A 时，才返回非零。|

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_ismbclower**|\<mbstring.h>|
|**_ismbclower_l**|\<mbstring.h>|
|**_ismbcupper**|\<mbstring.h>|
|**_ismbcupper_l**|\<mbstring.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[_ismbc 例程](../../c-runtime-library/ismbc-routines.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
