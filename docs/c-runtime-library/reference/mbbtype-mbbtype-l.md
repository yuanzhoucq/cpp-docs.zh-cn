---
title: _mbbtype、_mbbtype_l
ms.date: 11/04/2016
apiname:
- _mbbtype
- _mbbtype_l
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
ms.openlocfilehash: a6d17b99e4314c2ab836a16129ab8a0e6ac7720e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467166"
---
# <a name="mbbtype-mbbtypel"></a>_mbbtype、_mbbtype_l

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

*c*<br/>
要测试的字符。

*type*<br/>
要测试的字节类型。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_mbbtype**返回字符串中字节的类型。 此判定与上下文相关，为指定的值*类型*，其中提供了控制测试条件。 *类型*是在字符串中的上一个字节的类型。 下表中的清单常量在 Mbctype.h 中定义。

|值*类型*|**_mbbtype**测试|返回值|*c*|
|---------------------|--------------------------|------------------|---------|
|1 以外的任何值|有效的单字节或前导字节|**_MBC_SINGLE** (0)|单字节 (0x20-0x7E、 0xA1-0xDF)|
|1 以外的任何值|有效的单字节或前导字节|**_MBC_LEAD** (1)|多字节字符的前导字节 (0x81-0x9F、 0xE0-0xFC)|
|1 以外的任何值|有效的单字节或前导字节|**_MBC_ILLEGAL**<br /><br /> ( -1)|无效的字符 (任何以外的值 0x20-0x7E 以及 0xA1-0xDF、 0x81-0x9F、 0xE0-0xFC|
|1|有效的结尾字节|**_MBC_TRAIL** (2)|多字节字符的尾随字节 (0x40-0x7E、 0x80-0xFC)|
|1|有效的结尾字节|**_MBC_ILLEGAL**<br /><br /> ( -1)|无效的字符 (任何以外的值 0x20-0x7E 以及 0xA1-0xDF、 0x81-0x9F、 0xE0-0xFC|

## <a name="remarks"></a>备注

**_Mbbtype**函数确定多字节字符中字节的类型。 如果的值*类型*是 1，以外的任何值 **_mbbtype**测试多字节字符的有效单字节或前导字节。 如果的值*类型*为 1， **_mbbtype**测试多字节字符的有效的结尾字节。

输出值受的设置**LC_CTYPE**的区域设置的类别设置影响; 请参阅[setlocale、 _wsetlocale](setlocale-wsetlocale.md)有关详细信息。 **_Mbbtype**依赖于区域设置的行为; 此函数版本使用当前区域设置 **_mbbtype_l**版本是完全相同，只不过它改用已传入的区域设置参数. 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在早期版本中， **_mbbtype**名为**chkctype**。 对于新代码，请使用 **_mbbtype**相反。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\*用作返回值的清单常量的定义。

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字节分类](../../c-runtime-library/byte-classification.md)<br/>
