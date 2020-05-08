---
title: __pctype_func
ms.date: 4/2/2020
api_name:
- __pctype_func
- _o___pctype_func
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: 67447823b0322e647784cdbe0f3f7228e1c5fb34
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919236"
---
# <a name="__pctype_func"></a>__pctype_func

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

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>另请参阅

[_pctype、_pwctype、_wctype、_mbctype、_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
