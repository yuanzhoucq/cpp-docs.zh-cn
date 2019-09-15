---
title: _set_controlfp
ms.date: 04/05/2018
api_name:
- _set_controlfp
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_controlfp
- _set_controlfp
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
ms.openlocfilehash: 4d39406db0f4c9ba6374776da62aea2dbb61e23d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948673"
---
# <a name="_set_controlfp"></a>_set_controlfp

设置浮点控制字。

## <a name="syntax"></a>语法

```C
void __cdecl _set_controlfp(
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>参数

*newControl*<br/>
新的控制字位值。

*mask*<br/>
要设置的新控制字位掩码。

## <a name="return-value"></a>返回值

无。

## <a name="remarks"></a>备注

**_Set_controlfp**函数类似于 **_control87**，但它仅将浮点控制字设置为*newControl*。 值中的位表示浮点控制状态。 浮点控制状态允许程序在浮点数学包中更改精度、舍入和无穷模式。 还可以使用 **_set_controlfp**屏蔽或取消屏蔽浮点异常。 有关详细信息，请参阅 [_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)。

使用[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)进行编译时，不推荐使用此函数，因为公共语言运行时仅支持默认的浮点精度。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|兼容性|
|-------------|---------------------|-------------------|
|**_set_controlfp**|\<float.h>|仅限 x86 处理器|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)<br/>
