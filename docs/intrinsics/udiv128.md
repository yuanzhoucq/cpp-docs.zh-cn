---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 0e66bbe978199f47134aa288bdd2bac4eb3e332a
ms.sourcegitcommit: 2ce88de75e7681220ae09a0ab13056f22f357a46
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982436"
---
# <a name="udiv128"></a>_udiv128

`_udiv128`内部函数将由 64 位无符号整数的 128 位无符号的整数。 返回值包含商和内部函数返回的指针参数通过余数。 `_udiv128` 是**特定于 Microsoft**。

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
[in]被除数的高 64 位。

*lowDividend* \
[in]被除数的低 64 位。

*divisor* \
[in]要除以的 64 位整数。

*remainder* \
[out]64 位整数位的其余部分。

## <a name="return-value"></a>返回值

商的 64 位。

## <a name="remarks"></a>备注

将传递在 128 位被除数的高 64 位*highDividend*，并在较低的 64 位*lowDividend*。 内部函数将此值，从而*除数*。 将存储在其余部分中指向的 64 位无符号整数*余数*，并返回商 64 位。

`_udiv128`内部函数是在 Visual Studio 2019 RTM 中推出。

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_udiv128`|X64|\<immintrin.h>|

## <a name="see-also"></a>请参阅

[_div128](div128.md) \
[编译器内部函数](compiler-intrinsics.md)
