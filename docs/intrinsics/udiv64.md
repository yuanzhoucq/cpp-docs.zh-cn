---
title: _udiv64
ms.date: 04/17/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: 73a29b180eeda49a9a25e9e568d25c7563234fad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390147"
---
# <a name="udiv64"></a>_udiv64

`_udiv64`内部函数将由 32 位无符号整数的 64 位无符号的整数。 返回值包含商和内部函数返回的指针参数通过余数。 `_udiv64` 是**特定于 Microsoft**。

## <a name="syntax"></a>语法

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>参数

*dividend*<br/>
[in]要除以的 64 位无符号的整数。

*divisor*<br/>
[in]要除以的 32 位无符号的整数。

*remainder*<br/>
[out]32 位无符号的整数余数。

## <a name="return-value"></a>返回值

商的 32 位。

## <a name="remarks"></a>备注

`_udiv64`内部函数划分*被除数*通过*除数*。 将存储在其余部分中指向的 32 位无符号整数*余数*，并返回 32 位的商。

`_udiv64`内部函数是在 Visual Studio 2019 RTM 中推出。

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_udiv64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>请参阅

[_div64](div64.md) \
[编译器内部函数](compiler-intrinsics.md)
