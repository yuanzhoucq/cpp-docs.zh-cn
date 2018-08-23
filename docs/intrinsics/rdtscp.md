---
title: __rdtscp |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtscp
dev_langs:
- C++
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a98f1e84f3ef09d3cef5d45028374b93887fc6d4
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539199"
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
 [out] `Aux`  
 将包含特定于计算机的寄存器的内容的位置的指针`TSC_AUX[31:0]`。  
  
## <a name="return-value"></a>返回值  
 64 位无符号的整数的计时周期计数。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__rdtscp`|AMD NPT 系列 0Fh 或更高版本|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 此内部函数生成`rdtscp`指令。 若要确定此指令的硬件支持，请调用`__cpuid`与内部`InfoType=0x80000001`，并检查的 27 位`CPUInfo[3] (EDX)`。 此位为否则如果支持该指令，则为 1 和 0。  如果你运行代码，使用此内部函数不支持的硬件上`rdtscp`指令，则结果不可预知。  
  
> [!CAUTION]
>  与不同`rdtsc`，`rdtscp`是序列化的说明; 不过，编译器可以将解决此问题的代码移动内部函数。  
  
 在这一代硬件 TSC 值的解释不同于在早期版本的 x64。  请参阅硬件手册，以获得详细信息。  
  
 中的值的含义`TSC_AUX[31:0]`取决于操作系统。  
  
## <a name="example"></a>示例  
  
```  
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
 高级微设备，inc.版权所有 2007保留所有权利。 重新生成具有高级微设备，inc.的权限  
  
## <a name="see-also"></a>请参阅  
 [__rdtsc](../intrinsics/rdtsc.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)