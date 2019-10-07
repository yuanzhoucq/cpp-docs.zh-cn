---
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 1d05c5d6e25540a5de1b2f8231697c9a738759ce
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216775"
---
# <a name="_div64"></a>_div64

`_div64`内部函数将64位整数除以32位整数。 返回值保留商, 内部函数通过指针参数返回余数。 `_div64`**特定于 Microsoft**。

## <a name="syntax"></a>语法

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>参数

*被除数* \
中要相除的64位整数。

*divisor* \
中要除以的32位整数。

*剩下* \
弄余数的32位整数位。

## <a name="return-value"></a>返回值

商的32位。

## <a name="remarks"></a>备注

内部函数除以*除数*。 `_div64` 它将余数存储在由*余数*指向的32位整数中, 并返回商的32位。

从 Visual Studio 2019 RTM 开始可以使用内部函数。`_div64`

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_div64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>请参阅

[_udiv64](udiv64.md) \
[编译器内部函数](compiler-intrinsics.md)
