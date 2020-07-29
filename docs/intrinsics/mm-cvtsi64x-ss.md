---
title: _mm_cvtsi64x_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: a8227fcb482267946ea7ba08ee352c43e1ac6f6e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217995"
---
# <a name="_mm_cvtsi64x_ss"></a>_mm_cvtsi64x_ss

**Microsoft 专用**

生成 x64 扩展版本的将64位整数转换为标量单精度浮点值（ `cvtsi2ss` ）指令。

## <a name="syntax"></a>语法

```C
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

### <a name="parameters"></a>参数

*的*\
中一个 **`__m128`** 包含四个单精度浮点值的结构。

*b*\
中要转换为浮点值的64位整数。

## <a name="return-value"></a>返回值

一个 **`__m128`** 结构，其第一个浮点值为转换的结果。 其他三个*值从中*复制不变。

## <a name="requirements"></a>要求

|Intrinsic|体系结构|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|X64|

**头文件** \<intrin.h>

## <a name="remarks"></a>备注

**`__m128`** 结构表示一个 xmm 寄存器，因此内部函数允许将值*b*从系统内存移到一个 xmm 寄存器中。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```cpp
// _mm_cvtsi64x_ss.cpp
// processor: x64

#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtsi64x_ss)

int main()
{
    __m128 a;
    __int64 b = 54;

    a.m128_f32[0] = 0;
    a.m128_f32[1] = 0;
    a.m128_f32[2] = 0;
    a.m128_f32[3] = 0;
    a = _mm_cvtsi64x_ss(a, b);

    printf_s( "%lf %lf %lf %lf\n",
              a.m128_f32[0], a.m128_f32[1],
              a.m128_f32[2], a.m128_f32[3] );
}
```

```Output
54.000000 0.000000 0.000000 0.000000
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__m128](../cpp/m128.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
