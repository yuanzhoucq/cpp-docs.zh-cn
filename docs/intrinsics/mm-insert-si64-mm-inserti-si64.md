---
title: _mm_insert_si64, _mm_inserti_si64
ms.date: 11/04/2016
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
ms.openlocfilehash: 062e7e56de16d8e8a18101dec0a8e9766e02967f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631010"
---
# <a name="mminsertsi64-mminsertisi64"></a>_mm_insert_si64, _mm_inserti_si64

**Microsoft 专用**

生成`insertq`指令，bits 从第二个操作数插入第一个操作数。

## <a name="syntax"></a>语法

```
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

#### <a name="parameters"></a>参数

*Source1*<br/>
[in]具有一个字段将插入其较低的 64 位中的输入数据的 128 位字段。

*Source2*<br/>
[in]具有要在其低位中插入的数据的 128 位字段。  有关`_mm_insert_si64`，还包含其高位中的字段描述符。

*长度*<br/>
[in]整数常量，指定要插入的字段的长度。

*Tuple*<br/>
[in]整数常量，它指定将插入数据的字段的最低有效位的索引。

## <a name="return-value"></a>返回值

128 位字段，其较低的 64 位包含原始的低 64 位`Source1`与指定的位字段替换为的低位`Source2`。 返回值的高 64 位未定义。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_mm_insert_si64`|SSE4a|
|`_mm_inserti_si64`|SSE4a|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此内部函数生成`insertq`指令，以插入位`Source2`到`Source1`。 有两个版本的此内部函数： `_mm_inserti_si64`，是即时的版本中，和`_mm_insert_si64`是非直接。  每个版本从 Source2 提取给定长度的位字段，并将其插入到 Source1。  提取的位都 Source2 的最低有效位。  这些位将插入字段 Source1 规定的长度和其最低有效位的索引。  长度和索引的值所求模 64，因此为-1 到 127 之间被解释为 63。 如果 （减少） 位索引和 （减少） 的字段长度的总和大于 64，则结果不确定。 字段长度为零的值被解释为 64。  如果字段长度和位索引的两个为零，bits 63:0`Source2`插入到`Source1`。  如果字段长度为零，但比索引为非零，则结果不确定。

在 _mm_insert_si64 调用，则字段长度包含在位 77:72 Source2 和 bits 69:64 中的索引。

如果您调用`_mm_inserti_si64`使用编译器无法确定为整数常量的参数，编译器将生成代码打包到 XMM 寄存器的这些值并调用`_mm_insert_si64`。

若要确定的硬件支持`insertq`指令调用`__cpuid`与内部`InfoType=0x80000001`，并检查的 6 位`CPUInfo[2] (ECX)`。 此位将否则如果支持该指令，则为 1 和 0。 如果你运行代码，使用此内部函数不支持的硬件上`insertq`指令，则结果不可预知。

## <a name="example"></a>示例

```
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

高级微设备，inc.版权所有 2007保留所有权利。 重新生成具有高级微设备，inc.的权限

## <a name="see-also"></a>请参阅

[_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)