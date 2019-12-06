---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: ddb46f33b0fccc1cedc2a704265b096ba715b506
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857991"
---
# <a name="_udiv64"></a>_udiv64

`_udiv64` 内部函数将64位无符号整数除以32位无符号整数。 返回值保留商，内部函数通过指针参数返回余数。 `_udiv64` 是**Microsoft 特定**的。

## <a name="syntax"></a>语法

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>参数

被*除数*\
中要相除的64位无符号整数。

*divisor*\
中要作为除数的32位无符号整数。

*余数*\
弄32位无符号整数余数。

## <a name="return-value"></a>返回值

商的32位。

## <a name="remarks"></a>备注

`_udiv64` 内部*函数除以* *除数*。 它将余数存储在由*余数*指向的32位无符号整数中，并返回商的32位。

从 Visual Studio 2019 RTM 开始，提供 `_udiv64` 内部函数。

## <a name="requirements"></a>需求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_udiv64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>另请参阅

[_div64](div64.md) \
[编译器内部函数](compiler-intrinsics.md)
