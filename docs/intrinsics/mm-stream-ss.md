---
title: _mm_stream_ss
ms.date: 11/04/2016
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 76c6c848351df773b9857b2f83726b64db982d9f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031191"
---
# <a name="mmstreamss"></a>_mm_stream_ss

**Microsoft 专用**

32 位数据而无需污染缓存写入内存位置中。

## <a name="syntax"></a>语法

```
void _mm_stream_ss(
   float * Dest,
   __m128 Source
);
```

#### <a name="parameters"></a>参数

*dest*<br/>
[out]指向写入源数据的位置的指针。

*源*<br/>
[in]包含一个 128 位数字`float`32 位在其下中写入值...

## <a name="return-value"></a>返回值

无。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此内部函数生成`movntss`指令。 若要确定此指令的硬件支持，请调用`__cpuid`与内部`InfoType=0x80000001`，并检查的 6 位`CPUInfo[2] (ECX)`。 此位为 1 时支持的指令，则和 0 否则。

如果你运行使用的代码`_mm_stream_ss`内部函数不支持的硬件上`movntss`指令，则结果不可预知。

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

高级微设备，inc.版权所有 2007保留所有权利。 重新生成具有高级微设备，inc.的权限

## <a name="see-also"></a>请参阅

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)<br/>
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)<br/>
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)<br/>
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)