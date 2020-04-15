---
title: _mbbtype、_mbbtype_l
ms.date: 4/2/2020
api_name:
- _mbbtype
- _mbbtype_l
- _o__mbbtype
- _o__mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
ms.openlocfilehash: 7e2e818ed70ec393e4f81008f76ca9efe9cfa7e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341401"
---
# <a name="_mbbtype-_mbbtype_l"></a>_mbbtype、_mbbtype_l

基于上一个字节返回字节类型。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _mbbtype(
   unsigned char c,
   int type
);
int _mbbtype_l(
   unsigned char c,
   int type,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*C*<br/>
要测试的字符。

*type*<br/>
要测试的字节类型。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_mbbtype**返回字符串中的字节类型。 此决策对上下文敏感，由*类型的值*指定，该值提供控件测试条件。 *类型*是字符串中前一个字节的类型。 下表中的清单常量在 Mbctype.h 中定义。

|*类型*值|**_mbbtype**测试|返回值|*C*|
|---------------------|--------------------------|------------------|---------|
|1 以外的任何值|有效的单字节或前导字节|**_MBC_SINGLE** （0）|单字节 （0x20 - 0x7E， 0xA1 - 0xDF）|
|1 以外的任何值|有效的单字节或前导字节|**_MBC_LEAD** （1）|多字节字符的引线字节 （0x81 - 0x9F， 0xE0 - 0xFC）|
|1 以外的任何值|有效的单字节或前导字节|**_MBC_ILLEGAL**<br /><br /> ( -1)|无效字符（除 0x20 - 0x7E、0xA1 - 0xDF、0x81 - 0x9F、0xE0 - 0xFC 外的任何值|
|1|有效的结尾字节|**_MBC_TRAIL** （2）|多字节字符的尾随字节 （0x40 - 0x7E， 0x80 - 0xFC）|
|1|有效的结尾字节|**_MBC_ILLEGAL**<br /><br /> ( -1)|无效字符（除 0x20 - 0x7E、0xA1 - 0xDF、0x81 - 0x9F、0xE0 - 0xFC 外的任何值|

## <a name="remarks"></a>备注

**_mbbtype**函数确定多字节字符中的字节类型。 如果*类型*的值是除 1 以外的任何值，**则_mbbtype**测试多字节字符的有效单字节或引线字节。 如果*类型*的值为 1，**则_mbbtype**测试多字节字符的有效跟踪字节。

输出值受区域设置**LC_CTYPE**类别设置的影响;有关详细信息[，请参阅集本地设置_wsetlocale。](setlocale-wsetlocale.md) 此函数**的_mbbtype**版本使用此与区域设置相关的行为的当前区域设置;**_mbbtype_l**版本相同，只是它使用传入区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在早期版本中 **，_mbbtype**被命名为**chkctype**。 对于新代码，请使用 **_mbbtype。**

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\*用作返回值的清单常量的定义。

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
