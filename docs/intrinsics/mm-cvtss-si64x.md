---
title: _mm_cvtss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: bc6e33da5ac7b25727f6e24c3af6e6a926b29847
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230501"
---
# <a name="_mm_cvtss_si64x"></a>_mm_cvtss_si64x

**Microsoft 专用**

生成 x64 扩展版本，将标量单精度浮点数转换为64位整数（ `cvtss2si` ）指令。

## <a name="syntax"></a>语法

```C
__int64 _mm_cvtss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>参数

*负值*\
中**`__m128`** 包含浮点值的结构。

## <a name="return-value"></a>返回值

64位整数，是第一个浮点值到整数的转换结果。

## <a name="requirements"></a>要求

|Intrinsic|体系结构|
|---------------|------------------|
|`_mm_cvtss_si64x`|X64|

**头文件** \<intrin.h>

## <a name="remarks"></a>备注

结构值的第一个元素转换为整数，并返回。 MXCSR 中的舍入控制位用于确定舍入行为。 默认舍入模式舍入为最接近的值，如果小数部分为0.5，则舍入为偶数。 由于该 **`__m128`** 结构表示一个 xmm 寄存器，因此它从 xmm 寄存器中获取一个值并将其写入系统内存。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```cpp
// _mm_cvtss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] =
                           { 101.25, 200.75, 300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvtss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__m128d](../cpp/m128d.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
