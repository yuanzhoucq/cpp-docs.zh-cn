---
title: _mm_stream_sd
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: 7f0c6457cc0806a0f1764300cffa1c9878b8a600
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217372"
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

*Source*\
中一个128位值, 该值包含`double`要写入其底部64位的值。

## <a name="return-value"></a>返回值

无。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

内部函数生成`movntsd`指令。 若要确定此指令的硬件支持, 请`__cpuid`调用`InfoType=0x80000001`内部, 并检查的`CPUInfo[2] (ECX)`第6位。 如果硬件支持此指令, 则此位为 1; 否则为0。

如果在不`movntsd`支持指令的硬件`_mm_stream_sd`上运行使用内部函数的代码, 则结果是不可预知的。

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

部分版权 2007, 由高级微设备, Inc。保留所有权利。 从高级微设备, Inc. 的权限重现。

## <a name="see-also"></a>请参阅

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)\
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
