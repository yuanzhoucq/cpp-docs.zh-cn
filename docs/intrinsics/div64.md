---
title: _div64
ms.date: 04/17/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: a221cc7cf0655a41873c6777aecd8a9b27131b74
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62264109"
---
# <a name="div64"></a>_div64

`_div64`内部函数将由 32 位整数的 64 位整数。 返回值包含商和内部函数返回的指针参数通过余数。 `_div64` 是**特定于 Microsoft**。

## <a name="syntax"></a>语法

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>参数

*dividend* \
[in]要除以的 64 位整数。

*divisor* \
[in]要除以的 32 位整数。

*remainder* \
[out]32 位整数位的其余部分。

## <a name="return-value"></a>返回值

商的 32 位。

## <a name="remarks"></a>备注

`_div64`内部函数划分*被除数*通过*除数*。 它将其余部分存储在由指向 32 位整数*余数*，并返回 32 位的商。

`_div64`内部函数是在 Visual Studio 2019 RTM 中推出。

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_div64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>请参阅

[_udiv64](udiv64.md) \
[编译器内部函数](compiler-intrinsics.md)
