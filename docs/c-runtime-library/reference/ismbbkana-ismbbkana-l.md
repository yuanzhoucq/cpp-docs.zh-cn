---
title: _ismbbkana、_ismbbkana_l
ms.date: 11/04/2016
api_name:
- _ismbbkana_l
- _ismbbkana
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
- _ismbbkana_l
- ismbbkana_l
- ismbbkana
- _ismbbkana
helpviewer_keywords:
- _ismbbkana_l function
- _ismbbkana function
- ismbbkana function
- ismbbkana_l function
ms.assetid: 64d4eb4a-205a-40ef-be35-ff9d77fabbaf
ms.openlocfilehash: 0ac05940f6ae9d0c0bd3cb2f6ea73fe301557be4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954151"
---
# <a name="_ismbbkana-_ismbbkana_l"></a>_ismbbkana、_ismbbkana_l

测试片假名符号，并且专门用于代码页 932。

## <a name="syntax"></a>语法

```C
int _ismbbkana(
   unsigned int c
);
int _ismbbkana_l(
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

如果整数*c*是片假名符号，则 **_ismbbkana**返回非零值; 如果不是，则返回0。 **_ismbbkana**对与区域设置相关的字符信息使用当前区域设置。 **_ismbbkana_l**是相同的，只不过它使用传入的区域设置对象。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_ismbbkana**|\<mbctype.h>|
|**_ismbbkana_l**|\<mbctype.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
