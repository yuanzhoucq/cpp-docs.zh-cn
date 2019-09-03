---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 6dabbc94260ef578eb1a58a1b289b4a4654decdd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219678"
---
# <a name="_udiv64"></a>_udiv64

`_udiv64`内部函数将64位无符号整数除以32位无符号整数。 返回值保留商, 内部函数通过指针参数返回余数。 `_udiv64`**特定于 Microsoft**。

## <a name="syntax"></a>语法

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>参数

*被除数*\
中要相除的64位无符号整数。

*divisor*\
中要作为除数的32位无符号整数。

*剩下*\
弄32位无符号整数余数。

## <a name="return-value"></a>返回值

商的32位。

## <a name="remarks"></a>备注

内部函数除以*除数*。 `_udiv64` 它将余数存储在由*余数*指向的32位无符号整数中, 并返回商的32位。

从 Visual Studio 2019 RTM 开始可以使用内部函数。`_udiv64`

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_udiv64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>请参阅

[_div64](div64.md) \
[编译器内部函数](compiler-intrinsics.md)
