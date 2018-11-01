---
title: _mbsbtype、_mbsbtype_l
ms.date: 11/04/2016
apiname:
- _mbsbtype_l
- _mbsbtype
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
ms.openlocfilehash: 5c2927b4e4b68b1284341fe7e767ec50feb21a44
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566798"
---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype、_mbsbtype_l

返回字符串中字节的类型。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*mbstr*<br/>
多字节字符序列的地址。

*count*<br/>
字符串头中的字节偏移量。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_mbsbtype**并 **_mbsbtype_l**返回一个整数值，该值指示指定的字节的测试结果。 下表中的清单常量在 Mbctype.h 中定义。

|返回值|字节类型|
|------------------|---------------|
|**_MBC_SINGLE** (0)|单字节字符。 例如，在代码页 932 中， **_mbsbtype**返回 0，如果指定的字节位于范围 0x20-0x7E 或 0xA1-0xDF。|
|**_MBC_LEAD** (1)|多字节字符的前导字节。 例如，在代码页 932 中， **_mbsbtype**返回 1，如果指定的字节位于范围 0x81-0x9F 或 0xE0-0xFC。|
|**_MBC_TRAIL** (2)|多字节字符的尾随字节。 例如，在代码页 932 中， **_mbsbtype**返回 2，如果指定的字节在 0x40-0x7E 或 0x80-0xFC。|
|**_MBC_ILLEGAL** (-1)|**NULL**字符串、 无效的字符或之前的字节偏移量位置处找到 null 字节*计数*中*mbstr*。|

## <a name="remarks"></a>备注

**_Mbsbtype**函数确定多字节字符字符串中字节的类型。 该函数将检查仅的字节偏移量位置处*计数*中*mbstr*，忽略指定字节前的无效字符。

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 无需此函数的版本 **_l**后缀的此区域设置相关的行为; 使用当前区域设置与版本 **_l**后缀是相同，但它使用传入的区域设置参数在相反。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果输入的字符串**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**并且该函数返回 **_MBC_ILLEGAL**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\*用作返回值的清单常量。

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
