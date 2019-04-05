---
title: _mm_extract_si64、_mm_extracti_si64
ms.date: 11/04/2016
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
ms.openlocfilehash: e77ca5589ed50a4199921603afec1d9888c6cca5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040207"
---
# <a name="mmextractsi64-mmextractisi64"></a>_mm_extract_si64、_mm_extracti_si64

**Microsoft 专用**

生成`extrq`指令，以指定的 bits 提取其第一个参数的低 64 位。

## <a name="syntax"></a>语法

```
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

#### <a name="parameters"></a>参数

*源*<br/>
[in]具有其较低的 64 位中的输入数据的 128 位字段。

*描述符*<br/>
[in]描述要提取的位字段一个 128 位字段。

*长度*<br/>
[in]一个整数，指定要提取的字段的长度。

*索引*<br/>
[in]一个整数，指定要提取的字段的索引

## <a name="return-value"></a>返回值

以其最低有效位为单位的提取字段与一个 128 位字段。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_mm_extract_si64`|SSE4a|
|`_mm_extracti_si64`|SSE4a|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此内部函数生成`extrq`指令，以提取中的位`Source`。有两个版本的此内部函数：`_mm_extracti_si64`是即时的版本中，和`_mm_extract_si64`是非直接。  从提取每个版本`Source`由其长度和其最低有效位的索引定义的位字段。 长度和索引的值所求模 64，因此为-1 到 127 之间被解释为 63。 如果 （减少） 的索引和 （减少） 的字段长度的总和超出 64 个，则结果不确定。 字段长度为零的值被解释为 64。 如果字段长度和位索引的两个为零，bits 63:0`Source`提取。 如果字段长度为零，但比索引为非零，则结果不确定。

在调用 _mm_extract_si64，`Descriptor`包含 bits 13:8 和 bits 5:0 中提取的数据的字段长度中的索引...

如果您调用`_mm_extracti_si64`使用编译器无法确定为整数常量的参数，编译器生成代码打包到 XMM 寄存器的这些值 (`Descriptor`) 并调用`_mm_extract_si64`。

若要确定的硬件支持`extrq`指令，调用`__cpuid`与内部`InfoType=0x80000001`并检查的 6 位`CPUInfo[2] (ECX)`。 此位将否则如果支持该指令，则为 1 和 0。 如果你运行使用不支持此内部硬件的代码`extrq`指令，则结果不可预知。

## <a name="example"></a>示例

```
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

高级微设备，inc.版权所有 2007保留所有权利。 重新生成具有高级微设备，inc.的权限

## <a name="see-also"></a>请参阅

[_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)