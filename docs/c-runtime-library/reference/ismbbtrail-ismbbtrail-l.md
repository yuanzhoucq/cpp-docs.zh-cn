---
title: _ismbbtrail、_ismbbtrail_l
ms.date: 4/2/2020
api_name:
- _ismbbtrail
- _ismbbtrail_l
- _o__ismbbtrail
- _o__ismbbtrail_l
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
- _ismbbtrail
- ismbbtrail
- _ismbbtrail_l
- ismbbtrail_l
helpviewer_keywords:
- ismbbtrail_l function
- _ismbbtrail function
- _ismbbtrail_l function
- ismbbtrail function
ms.assetid: dfdd0292-960b-4c1d-bf11-146e0fc80247
ms.openlocfilehash: 08229b4a35634193810f7c24a3f8749fba034872
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918679"
---
# <a name="_ismbbtrail-_ismbbtrail_l"></a>_ismbbtrail、_ismbbtrail_l

确定一个字节是否为多字节字符的尾随字节。

## <a name="syntax"></a>语法

```C
int _ismbbtrail(
   unsigned int c
);
int _ismbbtrail_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*ansi-c*<br/>
要测试的整数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果整数*c*是多字节字符的第二个字节， **_ismbbtrail**将返回一个非零值。 例如，仅在代码页 932 中，有效范围为 0x40 到 0x7E 以及 0x80 到 0xFC。

## <a name="remarks"></a>备注

**_ismbbtrail**将当前区域设置用于与区域设置相关的行为。 **_ismbbtrail_l**相同，只不过它使用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_ismbbtrail**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|
|**_ismbbtrail_l**|\<mbctype.h 1> 或 \<mbstring.h 1>|\<ctype.h>、* \<limits.h 1>、\<stdlib.h 1>|

\* 适用于测试条件的清单常量。

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
