---
title: __rdtscp
ms.date: 07/11/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: b8a31c6d19cd171cbe909c75a27c2389866bd578
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861113"
---
# <a name="rdtscp"></a>__rdtscp

**Microsoft 专用**

将生成`rdtscp`指令，将写入`TSC_AUX[31:0`] 到内存，并返回 64 位时间戳计数器 (`TSC)`结果。

## <a name="syntax"></a>语法

```
unsigned __int64 __rdtscp(
   unsigned int * Aux
);
```

#### <a name="parameters"></a>参数

*Aux*<br/>
[out]将包含特定于计算机的寄存器的内容的位置的指针`TSC_AUX[31:0]`。

## <a name="return-value"></a>返回值

64 位无符号的整数的计时周期计数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__rdtscp`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此内部函数生成`rdtscp`指令。 若要确定此指令的硬件支持，请调用`__cpuid`与内部`InfoType=0x80000001`，并检查的 27 位`CPUInfo[3] (EDX)`。 此位为否则如果支持该指令，则为 1 和 0。  如果你运行代码，使用此内部函数不支持的硬件上`rdtscp`指令，则结果不可预知。

此指令等待，直到已执行所有前面的说明和所有以前加载都是全局可见。 但是，它不是序列化的指令。 请参阅 Intel 和 AMD 手册，以获得详细信息。

中的值的含义`TSC_AUX[31:0]`取决于操作系统。

## <a name="example"></a>示例

```cpp
#include <intrin.h>
#include <stdio.h>
int main()
{
    unsigned __int64 i;
    unsigned int ui;
    i = __rdtscp(&ui);
    printf_s("%I64d ticks\n", i);
    printf_s("TSC_AUX was %x\n", ui);
}
```

```Output
3363423610155519 ticks
TSC_AUX was 0
```

**结束 Microsoft 专用**


## <a name="see-also"></a>请参阅

[__rdtsc](../intrinsics/rdtsc.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)