---
title: _mm_extract_si64、_mm_extracti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
ms.openlocfilehash: cfd7029966c29f876f0e4f671830e20e2eacc940
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217399"
---
# <a name="_mm_extract_si64-_mm_extracti_si64"></a>_mm_extract_si64、_mm_extracti_si64

**Microsoft 专用**

`extrq`生成指令以从其第一个参数的低64位提取指定位。

## <a name="syntax"></a>语法

```C
__m128i _mm_extract_si64(
   __m128i Source,
   __m128i Descriptor
);
__m128i _mm_extracti_si64(
   __m128i Source,
   int Length,
   int Index
);
```

### <a name="parameters"></a>参数

*Source*\
中一个128位字段, 其输入数据位于其较低的64位。

*描述符*\
中描述要提取的位域的128位字段。

*长短*\
中一个整数, 指定要提取的字段的长度。

*编入*\
中一个整数, 指定要提取的字段的索引。

## <a name="return-value"></a>返回值

一个128位字段, 其最小有效位包含已提取的字段。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

这些内部函数生成`extrq`指令, 以便*从源*中提取位。 有两个版本: `_mm_extracti_si64`是即时版本, 而`_mm_extract_si64`不是即时版本。 每个版本*从源*中提取由其长度定义的位域和最小有效位的索引。 长度和索引的值采用的是 mod 64, 因此-1 和127都解释为63。 如果 (减) 索引和 (减少) 字段长度之和大于 64, 则结果是不确定的。 如果字段长度为零, 则将其解释为64。 如果字段长度和位索引均为零, 则提取*源*的位63:0。 如果字段长度为零, 但位索引为非零, 则结果是不确定的。

在对的调用`_mm_extract_si64`中,*描述符*包含13:8 位的索引, 以及要在 bits 5:0 中提取的数据的字段长度。

如果使用编译器`_mm_extracti_si64`无法确定为整数常量的参数调用, 则编译器将生成代码以将这些值打包到一个 XMM 寄存器 (*描述符*) 并调用`_mm_extract_si64`。

若要确定`extrq`指令的硬件支持, 请`__cpuid`调用内部`InfoType=0x80000001` , 并检查的`CPUInfo[2] (ECX)`第6位。 如果支持指令, 则此位为 1; 否则为0。 如果运行的代码使用不支持`extrq`该指令的此内部硬件, 则结果是不可预知的。

## <a name="example"></a>示例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source, descriptor, result1, result2, result3;

int
main()
{
    source.ui64[0] =     0xfedcba9876543210ll;
    descriptor.ui64[0] = 0x0000000000000b1bll;

    result1.m = _mm_extract_si64 (source.m, descriptor.m);
    result2.m = _mm_extracti_si64(source.m, 27, 11);
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;
}
```

```Output
result1 = 0x30eca86
result2 = 0x30eca86
result3 = 0x30eca86
```

**结束 Microsoft 专用**

部分版权 2007, 由高级微设备, Inc。保留所有权利。 从高级微设备, Inc. 的权限重现。

## <a name="see-also"></a>请参阅

[_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
