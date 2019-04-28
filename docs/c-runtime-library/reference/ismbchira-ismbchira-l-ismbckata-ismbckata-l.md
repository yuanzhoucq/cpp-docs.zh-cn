---
title: _ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l
ms.date: 11/04/2016
apiname:
- _ismbckata
- _ismbchira_l
- _ismbchira
- _ismbckata_l
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
- ismbckata_l
- _ismbckata_l
- ismbckata
- ismbchira
- _ismbckata
- ismbchira_l
- _ismbchira_l
- _ismbchira
helpviewer_keywords:
- _ismbckata function
- _ismbchira function
- _ismbckata_l function
- Katakana
- ismbchira function
- _ismbchira_l function
- ismbchira_l function
- ismbdkata_l function
- Hiragana
- ismbckata function
ms.assetid: 2db388a2-be31-489b-81c8-f6bf3f0582d3
ms.openlocfilehash: d2a5d0336e5ed4ad8bbb19f8a259128ab33d004e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286728"
---
# <a name="ismbchira-ismbchiral-ismbckata-ismbckatal"></a>_ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l

**代码页 932 特定函数**

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _ismbchira(
   unsigned int c
);
int _ismbchira_l(
   unsigned int c,
   _locale_t locale
);
int _ismbckata(
   unsigned int c
);
int _ismbckata_l(
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

其中每个例程在字符满足测试条件时返回一个非零值，在不满足测试条件时回 0。 如果*c* < = 255 且存在相应 **_ismbb**例程 (例如， **_ismbcalnum**对应于 **_ismbbalnum**)，则结果是相应的返回值 **_ismbb**例程。

## <a name="remarks"></a>备注

其中每个函数都针对给定的条件测试给定的多字节字符。

使用这些函数的版本 **_l**后缀完全相同，只不过它们使用为其区域设置相关的行为而不是当前区域设置传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

|例程所返回的值|测试条件（仅代码页 932）|
|-------------|-------------------------------------------|
|**_ismbchira**|双字节平假名：0x829F<=*c*<=0x82F1.|
|**_ismbchira_l**|双字节平假名：0x829F<=*c*<=0x82F1.|
|**_ismbckata**|双字节片假名：0x8340<=*c*<=0x8396.|
|**_ismbckata_l**|双字节片假名：0x8340<=*c*<=0x8396.|

**END 特定于代码页 932** 

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_ismbchira**|\<mbstring.h>|
|**_ismbchira_l**|\<mbstring.h>|
|**_ismbckata**|\<mbstring.h>|
|**_ismbckata_l**|\<mbstring.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[_ismbc 例程](../../c-runtime-library/ismbc-routines.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
