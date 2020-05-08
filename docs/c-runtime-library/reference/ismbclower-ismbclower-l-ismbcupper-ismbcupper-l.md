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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: f33bb4d882031221a80dc3b86670916a2e77af66
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915708"
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

*ansi-c*<br/>
要测试的字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

其中每个例程在字符满足测试条件时返回一个非零值，在不满足测试条件时回 0。 如果*c*<= 255，并且存在相应的 **_ismbb**例程（例如， **_ismbcalnum**对应于 **_ismbbalnum**），则结果为相应 **_ismbb**例程的返回值。

## <a name="remarks"></a>备注

其中每个函数都针对给定的条件测试给定的多字节字符。

这些具有 **_l**后缀的函数的版本相同，只不过它们使用传入的区域设置，而不是其与区域设置相关的行为的当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

|例程|测试条件|代码页 932 示例|
|-------------|--------------------|---------------------------|
|**_ismbclower**|小写字母|当且仅当*c*是 ASCII 小写英文字母的单字节表示形式时返回非零值： 0x61<=*c*<= 0x7A。|
|**_ismbclower_l**|小写字母|当且仅当*c*是 ASCII 小写英文字母的单字节表示形式时返回非零值： 0x61<=*c*<= 0x7A。|
|**_ismbcupper**|大写字母|当且仅当*c*是 ASCII 大写字母英文字母的单字节表示形式时返回非零值：0x41 向<=*c*<= 0x5A。|
|**_ismbcupper_l**|大写字母|当且仅当*c*是 ASCII 大写字母英文字母的单字节表示形式时返回非零值：0x41 向<=*c*<= 0x5A。|

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

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
[本地](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
