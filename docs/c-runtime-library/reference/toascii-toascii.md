---
title: toascii、__toascii
ms.date: 11/04/2016
api_name:
- __toascii
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
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
ms.openlocfilehash: 09df829511b38b87cb41e32a59bee9f38a9b8f32
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957461"
---
# <a name="toascii-__toascii"></a>toascii、__toascii

通过截断将字符转换为 7 位 ASCII。

## <a name="syntax"></a>语法

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>参数

*c*<br/>
要转换的字符。

## <a name="return-value"></a>返回值

**__toascii**将*c*的值转换为7位 ASCII 范围并返回结果。 没有保留任何返回值以指示错误。

## <a name="remarks"></a>备注

**__Toascii**例程通过将给定字符截断为低序位7位，将该字符转换为 ASCII 字符。 未应用其他转换。

**__Toascii**例程定义为宏，除非定义了预处理器宏 _CTYPE_DISABLE_MACROS。 为实现向后兼容性，仅当未定义[ &#95; &#95;STDC&#95; ](../../preprocessor/predefined-macros.md)或将其定义为0时，才将**toascii**定义为宏;否则为未定义。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**toascii**、 **__toascii**|C：\<ctype.h><br /><br /> C++：\<cctype> 或 \<ctype.h>|

**Toascii**宏为 posix 扩展， **__toascii**是 Microsoft 特定的 posix 扩展实现。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
[to 函数](../../c-runtime-library/to-functions.md)<br/>
