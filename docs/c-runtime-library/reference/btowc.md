---
title: btowc
ms.date: 11/04/2016
api_name:
- btowc
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: 1f03fce8686f919af85ee3751cb9a0a3fca1ede7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943470"
---
# <a name="btowc"></a>btowc

确定整数是否表示初始位移状态中的有效单字节字符。

## <a name="syntax"></a>语法

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>参数

*character*<br/>
要测试的整数。

## <a name="return-value"></a>返回值

如果整数表示初始位移状态中的有效单字节字符，则将返回字符的宽字符表示形式。 如果整数是 EOF 或不是初始位移状态中的有效单字节字符，则返回 WEOF。 此函数的输出受当前**LC_TYPE**区域设置的影响。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**btowc**|\<stdio.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
