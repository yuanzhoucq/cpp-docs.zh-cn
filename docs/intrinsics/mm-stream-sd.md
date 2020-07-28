---
title: _mm_stream_sd
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: ec639004884d022fe6a827c2ec31d3201ea04657
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214212"
---
# <a name="_mm_stream_sd"></a>_mm_stream_sd

**Microsoft 专用**

在不污染缓存的情况下将64位数据写入内存位置。

## <a name="syntax"></a>语法

```C
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

### <a name="parameters"></a>参数

*目的*\
弄指向将写入源数据的位置的指针。

*源程序*\
中一个128位值，该值包含 **`double`** 要写入其底部64位的值。

## <a name="return-value"></a>返回值

无。

## <a name="requirements"></a>要求

|Intrinsic|体系结构|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**头文件** \<intrin.h>

## <a name="remarks"></a>备注

内部函数生成 `movntsd` 指令。 若要确定此指令的硬件支持，请调用 `__cpuid` 内部， `InfoType=0x80000001` 并检查的第6位 `CPUInfo[2] (ECX)` 。 如果硬件支持此指令，则此位为 1; 否则为0。

如果在 `_mm_stream_sd` 不支持指令的硬件上运行使用内部函数的代码 `movntsd` ，则结果是不可预知的。

## <a name="example"></a>示例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128d vals;
    double d[2];

    d[0] = -1.;
    d[1] = -2.;
    vals.m128d_f64[0] = 0.;
    vals.m128d_f64[1] = 1.;
    _mm_stream_sd(&d[1], vals);
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;
}
```

```Output
d[0] = -1, d[1] = 1
```

**结束 Microsoft 专用**

部分版权2007，由高级微设备，Inc。保留所有权利。 从高级微设备，Inc. 的权限重现。

## <a name="see-also"></a>另请参阅

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)\
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
