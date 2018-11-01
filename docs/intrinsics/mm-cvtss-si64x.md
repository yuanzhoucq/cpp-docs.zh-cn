---
title: _mm_cvtss_si64x
ms.date: 11/04/2016
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: 259e3933c831ba685fa9d00d0f6471975a31f2cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606838"
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x

**Microsoft 专用**

生成扩展的 x64 版本的转换标量单精度浮点数到 64 位整数 (`cvtss2si`) 指令。

## <a name="syntax"></a>语法

```
__int64 _mm_cvtss_si64x( 
   __m128 value 
);
```

#### <a name="parameters"></a>参数

*value*<br/>
[in]`__m128`结构，它包含浮点数。

## <a name="return-value"></a>返回值

一个 64 位整数的第一个浮点值转换为整数的结果。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_mm_cvtss_si64x`|X64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

转换为整数并返回结构值的第一个元素。 在 MXCSR 舍入的控制位用于确定舍入行为。 默认舍入模式为舍入到最近的如果小数部分为 0.5 则舍入为偶数。 因为`__m128`结构表示 XMM 寄存器 XMM 寄存器，此内部函数采用一个值，并将其写入到系统内存。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```
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

[__m128d](../cpp/m128d.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)