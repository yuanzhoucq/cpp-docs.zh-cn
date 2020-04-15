---
title: _ismbbkprint、_ismbbkprint_l
ms.date: 4/2/2020
api_name:
- _ismbbkprint
- _ismbbkprint_l
- _o__ismbbkprint
- _o__ismbbkprint_l
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
- _ismbbkprint_l
- ismbbkprint
- _ismbbkprint
- ismbbkprint_l
helpviewer_keywords:
- _ismbbkprint function
- ismbbkprint_l function
- ismbbkprint function
- _ismbbkprint_l function
ms.assetid: 8d1d3258-1e34-4365-81ed-97c95de25475
ms.openlocfilehash: e59d06678b2601375bf3174fa84bc261c350c4dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343628"
---
# <a name="_ismbbkprint-_ismbbkprint_l"></a>_ismbbkprint、_ismbbkprint_l

确定特定多字节字符是否为标点符号。

## <a name="syntax"></a>语法

```C
int _ismbbkprint(
   unsigned int c
);
int _ismbbkprint_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*C*<br/>
要测试的整数。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果整数*c*是非 ASCII 文本或非 ASCII 标点符号，**则_ismbbkprint**返回非零值;如果不是，则返回非零值。 例如，仅在代码页 932 中，_ismbbkprint 测试片假名字母数字或片假名标点（范围：0xA1 - 0xDF）****。 **_ismbbkprint**使用当前区域设置进行与区域设置相关的字符设置。 **_ismbbkprint_l**是相同的，只不过它使用传入区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

## <a name="remarks"></a>备注

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_ismbbkprint**|\<mbctype.h>|
|**_ismbbkprint_l**|\<mbctype.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
