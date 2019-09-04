---
title: __rdtscp
ms.date: 09/02/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: 4dcabd6ed0f7fb3f422927815cbdc91f2b4b9d43
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221319"
---
# <a name="__rdtscp"></a>__rdtscp

**Microsoft 专用**

生成指令、写入`TSC_AUX[31:0`] 到内存, 并返回64位时间戳计数器 (`TSC)` result。 `rdtscp`

## <a name="syntax"></a>语法

```C
unsigned __int64 __rdtscp(
   unsigned int * AUX
);
```

### <a name="parameters"></a>参数

*助*\
弄指向将包含计算机特定寄存器`TSC_AUX[31:0]`内容的位置的指针。

## <a name="return-value"></a>返回值

64位无符号整数滴答计数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__rdtscp`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

`__rdtscp`内部函数`rdtscp`生成指令。 若要确定此指令的硬件支持, 请`__cpuid`调用`InfoType=0x80000001`内部, 并选中的`CPUInfo[3] (EDX)`bit 27。 如果支持指令, 则此位为 1; 否则为0。  如果在不支持`rdtscp`指令的硬件上运行使用内部函数的代码, 则结果是不可预知的。

此指令将一直等待, 直到所有前面的指令都已执行并且以前的所有加载都是全局可见的。 但是, 它不是序列化指令。 有关详细信息, 请参阅 Intel 和 AMD 手册。

中`TSC_AUX[31:0]`的值的含义取决于操作系统。

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

[__rdtsc](../intrinsics/rdtsc.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
