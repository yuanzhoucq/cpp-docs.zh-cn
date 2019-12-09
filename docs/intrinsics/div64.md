---
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 59c5eae66f9e93cb88f9512e405376f2ef5f1ceb
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858017"
---
# <a name="_div64"></a>_div64

`_div64` 内部函数将64位整数除以32位整数。 返回值保留商，内部函数通过指针参数返回余数。 `_div64` 是**Microsoft 特定**的。

## <a name="syntax"></a>语法

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>参数

被*除数* \
中要相除的64位整数。

*divisor* \
中要除以的32位整数。

*余数* \
弄余数的32位整数位。

## <a name="return-value"></a>返回值

商的32位。

## <a name="remarks"></a>备注

`_div64` 内部*函数除以* *除数*。 它将余数存储在由*余数*指向的32位整数中，并返回商的32位。

从 Visual Studio 2019 RTM 开始，提供 `_div64` 内部函数。

## <a name="requirements"></a>需求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_div64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>另请参阅

[_udiv64](udiv64.md) \
[编译器内部函数](compiler-intrinsics.md)
