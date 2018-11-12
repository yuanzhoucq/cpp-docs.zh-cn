---
title: __pctype_func
ms.date: 11/04/2016
apiname:
- __pctype_func
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: fc0f4b0be80534744beda1fe7595293ceb002924
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444221"
---
# <a name="pctypefunc"></a>__pctype_func

检索指向字符分类信息数组的指针。

## <a name="syntax"></a>语法

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>返回值

指向字符分类信息数组的指针。

## <a name="remarks"></a>备注

字符分类表中的信息仅供内部使用，并且由对类型 `char` 的字符进行分类的各种函数使用。 有关详细信息，请参阅 [_pctype、_pwctype、_wctype、_mbctype、_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md) 中的 `Remarks` 部分。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>请参阅

[_pctype、_pwctype、_wctype、_mbctype、_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)