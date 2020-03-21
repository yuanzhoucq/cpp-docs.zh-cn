---
title: _InterlockedCompareExchange128 内部函数
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
- _InterlockedCompareExchange128_acq
- _InterlockedCompareExchange128_nf
- _InterlockedCompareExchange128_np
- _InterlockedCompareExchange128_rel
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: 6f6b36b238945f7d46e9817cdc85977d666e1e9b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077630"
---
# <a name="_interlockedcompareexchange128-intrinsic-functions"></a>_InterlockedCompareExchange128 内部函数

**Microsoft 专用**

执行128位互锁比较和交换。

## <a name="syntax"></a>语法

```C
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_acq(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_nf(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_np(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_rel(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

### <a name="parameters"></a>parameters

*目标*\
[in，out]指向目标的指针，它是被视为128位字段的 2 64 位整数数组。 目标数据必须是16字节的对齐方式，以避免出现一般保护错误。

*ExchangeHigh*\
中可以与目标的高位部分交换的64位整数。

*ExchangeLow*\
中可以与目标的低部分交换的64位整数。

*ComparandResult*\
[in，out]指向与目标进行比较的 2 64 位整数数组（被视为128位字段）的指针。  输出时，将用目标的原始值覆盖此数组。

## <a name="return-value"></a>返回值

如果128位比较字等于目标的原始值，则为1。 `ExchangeHigh` 和 `ExchangeLow` 覆盖128位目标。

如果比较字不等于目标的原始值，则为0。 目标的值是不变的，比较字的值将被目标的值覆盖。

## <a name="requirements"></a>要求

|Intrinsic|体系结构|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64、ARM64|
|`_InterlockedCompareExchange128_acq`、`_InterlockedCompareExchange128_nf`、`_InterlockedCompareExchange128_rel`|ARM64|
|`_InterlockedCompareExchange128_np`|x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

`_InterlockedCompareExchange128` 内部函数生成 `cmpxchg16b` 指令（带有 `lock` 前缀），以执行128位已锁定的比较和交换。 早期版本的 AMD 64 位硬件不支持此指令。 若要检查 `cmpxchg16b` 指令的硬件支持，请用 `InfoType=0x00000001 (standard function 1)`调用 `__cpuid` 内部。 如果支持指令，则 `CPUInfo[2]` （ECX）的第13位为1。

> [!NOTE]
> 始终覆盖 `ComparandResult` 的值。 在 `lock` 指令后，此内部函数立即将 `Destination` 的初始值复制到 `ComparandResult`中。 出于此原因，`ComparandResult` 和 `Destination` 应指向不同的内存位置，以避免意外的行为。

尽管可以使用 `_InterlockedCompareExchange128` 进行低级别线程同步，但如果可以使用较小的同步函数（如其他 `_InterlockedCompareExchange` 内部函数），则无需在超过128位的情况下进行同步。 如果要在内存中访问128位值，请使用 `_InterlockedCompareExchange128`。

如果在不支持 `cmpxchg16b` 指令的硬件上运行使用内部函数的代码，则结果是不可预知的。

在 ARM 平台上，可以使用带 `_acq` 和 `_rel` 后缀的内部函数获取和发布语义，例如在临界区的起始位置。 带有 `_nf` （"无围墙"）后缀的 ARM 内部函数不能充当内存屏障。

带 `_np`（“无预取”）后缀的函数可以阻止编译器插入可能的预取操作。

此例程仅作为内部函数提供。

## <a name="example"></a>示例

此示例使用 `_InterlockedCompareExchange128` 将 2 64 位整数数组的高位字替换为其高位字和下限的总和，并递增下一字。 对 `BigInt.Int` 数组的访问是原子性的，但此示例使用单个线程并忽略锁定以简化。

```cpp
// cmpxchg16b.c
// processor: x64
// compile with: /EHsc /O2
#include <stdio.h>
#include <intrin.h>

typedef struct _LARGE_INTEGER_128 {
    __int64 Int[2];
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;

volatile LARGE_INTEGER_128 BigInt;

// This AtomicOp() function atomically performs:
//   BigInt.Int[1] += BigInt.Int[0]
//   BigInt.Int[0] += 1
void AtomicOp ()
{
    LARGE_INTEGER_128 Comparand;
    Comparand.Int[0] = BigInt.Int[0];
    Comparand.Int[1] = BigInt.Int[1];
    do {
        ; // nothing
    } while (_InterlockedCompareExchange128(BigInt.Int,
                                            Comparand.Int[0] + Comparand.Int[1],
                                            Comparand.Int[0] + 1,
                                            Comparand.Int) == 0);
}

// In a real application, several threads contend for the value
// of BigInt.
// Here we focus on the compare and exchange for simplicity.
int main(void)
{
   BigInt.Int[1] = 23;
   BigInt.Int[0] = 11;
   AtomicOp();
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",
      BigInt.Int[1],BigInt.Int[0]);
}
```

```Output
BigInt.Int[1] = 34, BigInt.Int[0] = 12
```

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[_InterlockedCompareExchange 内部函数](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)\
[与 x86 编译器冲突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
