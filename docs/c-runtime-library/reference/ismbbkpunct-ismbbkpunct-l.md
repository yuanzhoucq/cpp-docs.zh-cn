---
title: _ismbbkpunct、_ismbbkpunct_l
ms.date: 11/04/2016
api_name:
- _ismbbkpunct_l
- _ismbbkpunct
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ismbbkpunct_l
- _ismbbkpunct_l
- ismbbkpunct
- _ismbbkpunct
helpviewer_keywords:
- _ismbbkpunct_l function
- ismbbkpunct_l function
- ismbbkpunct function
- _ismbbkpunct function
ms.assetid: a04c59cd-5ca7-4296-bec0-2b0d7f04edd0
ms.openlocfilehash: 35f09013fbbe522a1eb747f2d2131a5fbb23f765
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954090"
---
# <a name="_ismbbkpunct-_ismbbkpunct_l"></a>_ismbbkpunct、_ismbbkpunct_l

检查多字节字符是否为标点字符。

## <a name="syntax"></a>语法

```C
int _ismbbkpunct(
   unsigned int c
);
int _ismbbkpunct_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*c*<br/>
要测试的整数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果整数*c*是非 ASCII 标点符号，则 **_ismbbkpunct**将返回一个非零值，如果不是，则返回0。 例如，仅在代码页 932 中，_ismbbkpunct 测试片假名标点。 **_ismbbkpunct**为任何与区域设置相关的字符设置使用当前区域设置。 **_ismbbkpunct_l**是相同的，只不过它使用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_ismbbkpunct**|\<mbctype.h>|
|**_ismbbkpunct_l**|\<mbctype.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
