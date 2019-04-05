---
title: _mm_stream_sd
ms.date: 11/04/2016
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: 3555b71e15d6f9c618a83f573d6da3cda9e7b705
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023511"
---
# <a name="mmstreamsd"></a>_mm_stream_sd

**Microsoft 专用**

64 位数据而无需污染缓存写入内存位置中。

## <a name="syntax"></a>语法

```
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

#### <a name="parameters"></a>参数

*dest*<br/>
[out]指向源数据将写入的位置的指针。

*源*<br/>
[in]128 位值，该值包含`double`64 位在其下中写入值...

## <a name="return-value"></a>返回值

无。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此内部函数生成`movntsd`指令。 若要确定此指令的硬件支持，请调用`__cpuid`与内部`InfoType=0x80000001`，并检查的 6 位`CPUInfo[2] (ECX)`。 如果硬件支持此指令和 0 否则，此位为 1。

如果你运行使用的代码`_mm_stream_sd`内部函数不支持的硬件上`movntsd`指令，则结果不可预知。

## <a name="example"></a>示例

```
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

高级微设备，inc.版权所有 2007保留所有权利。 重新生成具有高级微设备，inc.的权限

## <a name="see-also"></a>请参阅

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)<br/>
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)<br/>
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)