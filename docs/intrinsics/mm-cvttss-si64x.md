---
title: _mm_cvttss_si64x
ms.date: 11/04/2016
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 2097ec50eca68cbe5735d30e772644552ab0df3b
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329015"
---
# <a name="mmcvttsssi64x"></a>_mm_cvttss_si64x

**Microsoft 专用**

发出扩展的 x64 版本的截断为 64 位整数的单精度浮点数字使用 Convert (`cvttss2si`) 指令。

## <a name="syntax"></a>语法

```
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

#### <a name="parameters"></a>参数

*value*<br/>
[in]`__m128`结构，它包含单精度浮点值。

## <a name="return-value"></a>返回值

第一个浮点值转换为 64 位整数的结果。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_mm_cvttss_si64x`|X64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

内部函数不同于`_mm_cvtss_si64x`仅在于不精确的转换将向零截断。 因为`__m128`结构表示 XMM 寄存器，生成的指令将数据从 XMM 寄存器移动到系统内存。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```
// _mm_cvttss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvttss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] = { 101.5, 200.75,
                                          300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvttss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__m128](../cpp/m128.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)