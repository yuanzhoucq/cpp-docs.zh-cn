---
title: _mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l
ms.date: 11/04/2016
apiname:
- _mbctolower_l
- _mbctoupper_l
- _mbctoupper
- _mbctolower
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
- mbctoupper_l
- mbctolower_l
- _mbctolower
- _mbctolower_l
- _mbctoupper
- mbctoupper
- mbctolower
- _mbctoupper_l
helpviewer_keywords:
- _mbctolower function
- mbctolower_l function
- totupper function
- _mbctoupper function
- totlower function
- _mbctoupper_l function
- mbctolower function
- _totupper function
- _mbctolower_l function
- mbctoupper_l function
- _totlower function
- mbctoupper function
ms.assetid: 787fab71-3224-4ed7-bc93-4dcd8023fc54
ms.openlocfilehash: e620af526e5f0af02868bba4ba635e9ed6e34ff6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539680"
---
# <a name="mbctolower-mbctolowerl-mbctoupper-mbctoupperl"></a>_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l

测试和转换多字节字符的大小写形式。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
unsigned int _mbctolower(
   unsigned int c
);
unsigned int _mbctolower_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbctoupper(
   unsigned int c
);
unsigned int _mbctoupper_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*c*<br/>
要转换的多字节字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

每个函数返回转换的字符*c*如有可能。 否则它返回的字符*c*不变。

## <a name="remarks"></a>备注

这些函数将测试一个字符*c*和，如果可能，请应用下列转换之一。

|例程|转换|
|--------------|--------------|
|**_mbctolower**， **_mbctolower_l**|大写字符到小写字符。|
|**_mbctoupper**， **_mbctoupper_l**|小写字符到大写字符。|

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 无需此函数的版本 **_l**后缀的此区域设置相关的行为; 使用当前区域设置与版本 **_l**后缀是完全相同，只不过它使用的区域设置参数改为传入。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在上一版本中， **_mbctolower**调用**jtolower**，并 **_mbctoupper**调用**jtoupper**。 对于新代码，请改用新名称。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_totlower**|**tolower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_t**|
|**_totupper**|**toupper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**toupper_l**|**_mbctoupper_l**|**_towupper_l**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|--------------|---------------------|
|**_mbctolower**， **_mbctolower_l**|\<mbstring.h>|
|**_mbctoupper**， **_mbctoupper_l**|\<mbstring.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[_mbbtombc、_mbbtombc_l](mbbtombc-mbbtombc-l.md)<br/>
[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)<br/>
[_mbctombb、_mbctombb_l](mbctombb-mbctombb-l.md)<br/>
