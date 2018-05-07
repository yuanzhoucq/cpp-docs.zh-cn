---
title: _InterlockedCompareExchange128 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
dev_langs:
- C++
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f491f59289a2e3b951e1bad60f260a801ea68bea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="interlockedcompareexchange128"></a>_InterlockedCompareExchange128
**Microsoft 专用**  
  
 执行 128 位联锁的比较和交换。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned char _InterlockedCompareExchange128(  
   __int64 volatile * Destination,  
   __int64 ExchangeHigh,  
   __int64 ExchangeLow,  
   __int64 * ComparandResult  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in, out] `Destination`  
 指向目标，目标是两个 64 位整数的数组视为一个 128 位字段。 目标数据必须是 16 字节对齐以避免了一般性保护错误。  
  
 [in] `ExchangeHigh`  
 一个 64 位整数，它可能与目标的高部分进行交换。  
  
 [in] `ExchangeLow`  
 一个 64 位整数，它可能与目标的低部分进行交换。  
  
 [in, out] `ComparandResult`  
 指向数组 （视为一个 128 位字段） 的两个 64 位整数的指针以将与目标进行比较。  在输出时，这会覆盖目标的原始值。  
  
## <a name="return-value"></a>返回值  
 如果 128 位字等于目标的原始值为 1。 `ExchangeHigh` 和`ExchangeLow`覆盖 128 位目标。  
  
 如果该比较字不等于目标的原始值为 0。 目标值不变，且使用的目标值覆盖该比较字的值。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_InterlockedCompareExchange128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 此内部函数生成`cmpxchg16b`指令 (与`lock`前缀) 执行 128 位锁定的比较和交换。 AMD 64 位硬件的早期版本不支持此指令。 若要检查的硬件支持`cmpxchg16b`指令，请调用`__cpuid`与内部`InfoType=0x00000001 (standard function 1)`。 位 13 `CPUInfo[2]` (ECX) 为 1，如果该指令受支持。  
  
> [!NOTE]
>  值`ComparandResult`始终覆盖。 后`lock`指令，此内部函数会立即将复制的初始值`Destination`到`ComparandResult`。 为此，`ComparandResult`和`Destination`应指向不同的内存位置，为避免意外的行为。  
  
 尽管可以使用`_InterlockedCompareExchange128`的低等级线程同步，你不需要同步超过 128 位，如果你可以使用较小的同步函数 (如其他`_InterlockedCompareExchange`内部函数) 相反。 使用`_InterlockedCompareExchange128`如果您希望对内存中的 128 位值的原子访问。  
  
 如果你运行代码使用此内部函数不支持的硬件上`cmpxchg16b`指令，则结果不可预知。  
  
 此例程是仅用作内部函数。  
  
## <a name="example"></a>示例  
 此示例使用`_InterlockedCompareExchange128`的两个 64 位整数数组的高位字替换其高和较低的字的总和，又可以增加低位字。 对 BigInt.Int 数组的访问权限是原子操作，但此示例使用单个线程并忽略为简单起见锁定。  
  
```  
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
 高级 Micro 设备，inc.版权所有 2007保留所有权利。 重新生成具有高级 Micro 设备，Inc.的权限  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [_InterlockedCompareExchange 内部函数](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)   
 [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)