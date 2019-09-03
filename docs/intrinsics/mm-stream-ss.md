---
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 005f4f697d64f6ea68b35dc32daf1217be463a2a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217348"
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

*Source*\
中一个128位数字, 其中包含要`float`在其下32位写入的值。

## <a name="return-value"></a>返回值

无。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

内部函数生成`movntss`指令。 若要确定此指令的硬件支持, 请`__cpuid`调用`InfoType=0x80000001`内部, 并检查的`CPUInfo[2] (ECX)`第6位。 当支持指令时, 此位为 1; 否则为0。

如果在不`movntss`支持指令的硬件`_mm_stream_ss`上运行使用内部函数的代码, 则结果是不可预知的。

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

部分版权 2007, 由高级微设备, Inc。保留所有权利。 从高级微设备, Inc. 的权限重现。

## <a name="see-also"></a>请参阅

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
