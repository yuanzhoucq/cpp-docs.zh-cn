---
title: __shiftleft128
ms.date: 09/02/2019
f1_keywords:
- __shiftleft128
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
ms.openlocfilehash: 5da9ac81cedbdd24e10eb438892f88510c32ca24
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218001"
---
# <a name="__shiftleft128"></a>__shiftleft128

**Microsoft 专用**

将 128 位数量（表示为两个 64 位数量 `LowPart` 和 `HighPart`）按 `Shift` 指定的位数左移，返回高 64 位结果。

## <a name="syntax"></a>语法

```C
unsigned __int64 __shiftleft128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

### <a name="parameters"></a>参数

*LowPart*\
中要移位的128位数量的低64位。

*Largeint.highpart*\
中要移位的128位数量的高64位。

*格*\
中要移位的位数。

## <a name="return-value"></a>返回值

高 64 位的结果。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__shiftleft128`|X64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

*移位*值始终为模数 64, 因此, 例如`__shiftleft128(1, 0, 64)`, 如果调用, 该函数将`0`向左移动低部分`0`位并返回的上限, 而不`1`是预期的情况。

## <a name="example"></a>示例

```C
// shiftleft128.c
// processor: IPF, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__shiftleft128, __shiftright128)

int main()
{
    unsigned __int64 i = 0x1I64;
    unsigned __int64 j = 0x10I64;
    unsigned __int64 ResultLowPart;
    unsigned __int64 ResultHighPart;

    ResultLowPart = i << 1;
    ResultHighPart = __shiftleft128(i, j, 1);

    // concatenate the low and high parts padded with 0's
    // to display correct hexadecimal 128 bit values
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);

    ResultHighPart = j >> 1;
    ResultLowPart = __shiftright128(i, j, 1);

    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);
}
```

```Output
0x100000000000000001 << 1 = 0x200000000000000002
0x100000000000000001 >> 1 = 0x080000000000000000
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__shiftright128](../intrinsics/shiftright128.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
