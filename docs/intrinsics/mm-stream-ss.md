---
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: ef1a2045a20070b667d416175826e5377fe30ef6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215980"
---
# <a name="_mm_stream_ss"></a>_mm_stream_ss

**Microsoft 专用**

在不污染缓存的情况下将32位数据写入内存位置。

## <a name="syntax"></a>语法

```C
void _mm_stream_ss(
   float * Destination,
   __m128 Source
);
```

### <a name="parameters"></a>参数

*位置*\
弄指向写入源数据的位置的指针。

*源程序*\
中一个128位数字，其中包含 **`float`** 要在其下32位写入的值。

## <a name="return-value"></a>返回值

无。

## <a name="requirements"></a>要求

|Intrinsic|体系结构|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**头文件** \<intrin.h>

## <a name="remarks"></a>备注

内部函数生成 `movntss` 指令。 若要确定此指令的硬件支持，请调用 `__cpuid` 内部， `InfoType=0x80000001` 并检查的第6位 `CPUInfo[2] (ECX)` 。 当支持指令时，此位为 1; 否则为0。

如果在 `_mm_stream_ss` 不支持指令的硬件上运行使用内部函数的代码 `movntss` ，则结果是不可预知的。

## <a name="example"></a>示例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**结束 Microsoft 专用**

部分版权2007，由高级微设备，Inc。保留所有权利。 从高级微设备，Inc. 的权限重现。

## <a name="see-also"></a>另请参阅

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
