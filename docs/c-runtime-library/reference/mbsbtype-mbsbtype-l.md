---
title: _mbsbtype、_mbsbtype_l
ms.date: 4/2/2020
api_name:
- _mbsbtype_l
- _mbsbtype
- _o__mbsbtype
- _o__mbsbtype_l
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
ms.openlocfilehash: d71a061d9af5028c9bc6b4008f9904606a233592
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340878"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype、_mbsbtype_l

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

*姆布斯特*<br/>
多字节字符序列的地址。

*count*<br/>
字符串头中的字节偏移量。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_mbsbtype****和_mbsbtype_l**返回一个整数值，指示指定字节上的测试结果。 下表中的清单常量在 Mbctype.h 中定义。

|返回值|字节类型|
|------------------|---------------|
|**_MBC_SINGLE** （0）|单字节字符。 例如，在代码页 932 中，如果指定的字节在 0x20 - 0x7E 或 0xA1 - 0xDF 范围内 **，_mbsbtype**返回 0。|
|**_MBC_LEAD** （1）|多字节字符的前导字节。 例如，在代码页 932 中，如果指定的字节在 0x81 - 0x9F 或 0xE0 - 0xFC 范围内 **，_mbsbtype**返回 1。|
|**_MBC_TRAIL** （2）|多字节字符的尾随字节。 例如，在代码页 932 中，如果指定的字节在 0x40 - 0x7E 或 0x80 - 0xFC 范围内 **，_mbsbtype**返回 2。|
|**_MBC_ILLEGAL** （-1）|**在**偏移*计数**（mbstr）* 的字节之前找到的 NULL 字符串、无效字符或空字节。|

## <a name="remarks"></a>备注

**_mbsbtype**函数确定多字节字符串中的字节类型。 函数仅检查偏移*计数**（mbstr）* 的字节，忽略指定字节之前的无效字符。

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)****。 没有 **_l**后缀的函数版本使用此与区域设置相关的行为的当前区域设置;具有 **_l**后缀的版本是相同的，只不过它使用传入区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果输入字符串为**NULL，** 则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行 **，errno**将设置为**EINVAL，** 函数返回 **_MBC_ILLEGAL**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\*用作返回值的清单常量。

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
