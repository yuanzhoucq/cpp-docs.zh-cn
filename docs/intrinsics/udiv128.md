---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 5e8cc9ca3dbf19a04d07edb1d73df84f2e29a5c3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857978"
---
# <a name="_udiv128"></a>_udiv128

`_udiv128` 内部函数将128位无符号整数除以64位无符号整数。 返回值保留商，内部函数通过指针参数返回余数。 `_udiv128` 是**Microsoft 特定**的。

## <a name="syntax"></a>语法

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>参数

*highDividend* \
中被除数的高64位。

*lowDividend* \
中被除数的低64位。

*divisor* \
中要除以的64位整数。

*余数* \
弄余数的64位整数位。

## <a name="return-value"></a>返回值

商的64位。

## <a name="remarks"></a>备注

传递*highDividend*中的128位的上限64位，以及*lowDividend*中的较低64位。 内部函数用*除数*除以此值。 它将余数存储在由*余数*指向的64位无符号整数中，并返回商的64位。

从 Visual Studio 2019 RTM 开始，提供 `_udiv128` 内部函数。

## <a name="requirements"></a>需求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_udiv128`|x64|\<immintrin.h>|

## <a name="see-also"></a>另请参阅

[_div128](div128.md) \
[编译器内部函数](compiler-intrinsics.md)
