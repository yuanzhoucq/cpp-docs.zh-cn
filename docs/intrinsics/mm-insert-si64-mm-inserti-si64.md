---
title: _mm_insert_si64, _mm_inserti_si64
ms.date: 09/02/2019
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
ms.openlocfilehash: 08469ad8049df2a07f0e66d650c1ca3118f8b980
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221774"
---
# <a name="_mm_insert_si64-_mm_inserti_si64"></a>_mm_insert_si64, _mm_inserti_si64

**Microsoft 专用**

`insertq`生成指令, 以将位从其第二个操作数插入第一个操作数。

## <a name="syntax"></a>语法

```C
__m128i _mm_insert_si64(
   __m128i Source1,
   __m128i Source2
);
__m128i _mm_inserti_si64(
   __m128i Source1,
   __m128i Source2
   int Length,
   int Index
);
```

### <a name="parameters"></a>参数

*Source1*\
中一个128位字段, 它具有在其下插入字段的位于其较低64位的输入数据。

*Source2*\
中一个包含要在其低位中插入的数据的128位字段。  对于`_mm_insert_si64`, 还包含其高位中的字段描述符。

*长短*\
中指定要插入的字段长度的整数常量。

*编入*\
中一个整数常量, 它指定要将数据插入到其中的字段的最小有效位的索引。

## <a name="return-value"></a>返回值

128位字段, 其64位包含*Source1*的原始低64位, 并且指定的位域由*Source2*的低位替换。 返回值的上限64位未定义。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

这些内部函数生成`insertq`指令, 以便将*Source2*中的位插入到*Source1*中。 有两个版本: `_mm_inserti_si64`, 是即时版本`_mm_insert_si64` , 是非直接版本。 每个版本从 Source2 中提取给定长度的位域, 并将其插入到 Source1 中。  提取的位是 Source2 的最小有效位。  将在其中插入这些位的字段 Source1 由长度和最小有效位的索引定义。  长度和索引的值采用的是 mod 64, 因此-1 和127都解释为63。 如果 (减) 位索引和 (减少) 字段长度之和大于 64, 则结果是不确定的。 如果字段长度为零, 则将其解释为64。 如果字段长度和位索引均为零, 则将*Source2*的位63:0 插入到*Source1*中。 如果字段长度为零, 但位索引不为零, 则结果是不确定的。

在对 _mm_insert_si64 的调用中, 字段长度包含在 Source2 的 bits 77:72 和 bits 69:64 中的索引内。

如果使用编译器`_mm_inserti_si64`无法确定为整数常量的参数调用, 则编译器将生成代码以便将这些值打包到一个 XMM 寄存器并调用。 `_mm_insert_si64`

若要确定`insertq`指令的硬件支持, 请`__cpuid`调用内部`InfoType=0x80000001` , 并检查的`CPUInfo[2] (ECX)`第6位。 如果支持指令, 则此位为 1; 否则为0。 如果在不支持`insertq`指令的硬件上运行使用内部函数的代码, 则结果是不可预知的。

## <a name="example"></a>示例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

union {
    __m128i m;
    unsigned __int64 ui64[2];
} source1, source2, source3, result1, result2, result3;

int
main()
{

    __int64 mask;

    source1.ui64[0] = 0xffffffffffffffffll;
    source2.ui64[0] = 0xfedcba9876543210ll;
    source2.ui64[1] = 0xc10;
    source3.ui64[0] = source2.ui64[0];

    result1.m = _mm_insert_si64 (source1.m, source2.m);
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);
    mask = 0xffff << 12;
    mask = ~mask;
    result3.ui64[0] = (source1.ui64[0] & mask) |
                      ((source2.ui64[0] & 0xffff) << 12);

    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;
    cout << "result2 = 0x" << result2.ui64[0] << endl;
    cout << "result3 = 0x" << result3.ui64[0] << endl;

}
```

```Output
result1 = 0xfffffffff3210fff
result2 = 0xfffffffff3210fff
result3 = 0xfffffffff3210fff
```

**结束 Microsoft 专用**

部分版权 2007, 由高级微设备, Inc。保留所有权利。 从高级微设备, Inc. 的权限重现。

## <a name="see-also"></a>请参阅

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
