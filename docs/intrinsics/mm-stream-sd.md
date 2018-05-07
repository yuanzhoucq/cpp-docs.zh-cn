---
title: _mm_stream_sd |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_stream_sd
dev_langs:
- C++
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e8a65066ad19b78319867782255d70da8d5b721
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mmstreamsd"></a>_mm_stream_sd
**Microsoft 专用**  
  
 64 位数据而无需污染缓存写入内存位置中。  
  
## <a name="syntax"></a>语法  
  
```  
void _mm_stream_sd(  
   double * Dest,  
   __m128d Source  
);  
```  
  
#### <a name="parameters"></a>参数  
 [out] `Dest`  
 指向将在其中写入源数据的位置的指针。  
  
 [in] `Source`  
 一个 128 位值，其中包含`double`要写入在其下 64 位值...  
  
## <a name="return-value"></a>返回值  
 无。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_mm_stream_sd`|SSE4a|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 此内部函数生成`movntsd`指令。 若要确定此指令的硬件支持，请调用`__cpuid`与内部`InfoType=0x80000001`和检查的第 6 位`CPUInfo[2] (ECX)`。 如果硬件否则支持此指令和 0，则此位为 1。  
  
 如果运行的代码，使用`_mm_stream_sd`内部函数不支持的硬件上`movntsd`指令，则结果不可预知。  
  
## <a name="example"></a>示例  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
int main()  
{  
    __m128d vals;  
    double d[2];  
  
    d[0] = -1.;  
    d[1] = -2.;  
    vals.m128d_f64[0] = 0.;  
    vals.m128d_f64[1] = 1.;  
    _mm_stream_sd(&d[1], vals);  
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;  
}  
  
```  
  
```Output  
d[0] = -1, d[1] = 1  
```  
  
**结束 Microsoft 专用**  
 高级 Micro 设备，inc.版权所有 2007保留所有权利。 重新生成具有高级 Micro 设备，Inc.的权限  
  
## <a name="see-also"></a>请参阅  
 [_mm_stream_ss](../intrinsics/mm-stream-ss.md)   
 [_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)   
 [_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)