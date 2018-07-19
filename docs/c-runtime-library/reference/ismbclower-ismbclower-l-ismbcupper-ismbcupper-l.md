---
title: _ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
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
- _ismbcupper
- _ismbclower
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ef7b21cc10ca5e72a5054e34b0e228be89d74cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402229"
---
# <a name="ismbclower-ismbclowerl-ismbcupper-ismbcupperl"></a>_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l

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

*c*<br/>
要测试的字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

其中每个例程在字符满足测试条件时返回一个非零值，在不满足测试条件时回 0。 如果*c*< = 255，并且没有相应 **_ismbb**例程 (例如， **_ismbcalnum**对应于 **_ismbbalnum**)，则结果是相应的返回值 **_ismbb**例程。

## <a name="remarks"></a>备注

其中每个函数都针对给定的条件测试给定的多字节字符。

使用这些函数的版本 **_l**后缀是相同，只不过它们使用传递区域设置而不是当前区域设置其区域设置相关的行为。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

|例程|测试条件|代码页 932 示例|
|-------------|--------------------|---------------------------|
|**_ismbclower**|小写字母|返回非零当且仅当*c*是 ASCII 小写英文字母的单字节表示： 0x61 < =*c*< = 0x7A。|
|**_ismbclower_l**|小写字母|返回非零当且仅当*c*是 ASCII 小写英文字母的单字节表示： 0x61 < =*c*< = 0x7A。|
|**_ismbcupper**|大写字母|返回非零当且仅当*c*是 ASCII 大写英文字母的单字节表示： 0x41 向 < =*c*< = 0x5A。|
|**_ismbcupper_l**|大写字母|返回非零当且仅当*c*是 ASCII 大写英文字母的单字节表示： 0x41 向 < =*c*< = 0x5A。|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_ismbclower**|\<mbstring.h>|
|**_ismbclower_l**|\<mbstring.h>|
|**_ismbcupper**|\<mbstring.h>|
|**_ismbcupper_l**|\<mbstring.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[_ismbc 例程](../../c-runtime-library/ismbc-routines.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
