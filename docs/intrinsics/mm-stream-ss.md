---
title: _mm_stream_ss |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_stream_ss
dev_langs:
- C++
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef5910f47fdf9c058cfb4493c9df486749da18fc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714384"
---
# <a name="mmstreamss"></a>_mm_stream_ss  
  
**Microsoft 专用**  
  
 32 位数据而无需污染缓存写入内存位置中。  
  
## <a name="syntax"></a>语法  
  
```  
void _mm_stream_ss(  
   float * Dest,  
   __m128 Source  
);  
```  
  
#### <a name="parameters"></a>参数  
  
*dest*<br/>
[out]指向写入源数据的位置的指针。  
  
*Source*<br/>
[in]包含一个 128 位数字`float`32 位在其下中写入值...  
  
## <a name="return-value"></a>返回值  
  
 无。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_mm_stream_ss`|SSE4a|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
  
此内部函数生成`movntss`指令。 若要确定此指令的硬件支持，请调用`__cpuid`与内部`InfoType=0x80000001`，并检查的 6 位`CPUInfo[2] (ECX)`。 此位为 1 时支持的指令，则和 0 否则。  
  
如果你运行使用的代码`_mm_stream_ss`内部函数不支持的硬件上`movntss`指令，则结果不可预知。  
  
## <a name="example"></a>示例  
  
```cpp  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
int main()  
{  
    __m128 vals;  
    float f[4];  
  
    f[0] = -1.;  
    f[1] = -2.;  
    f[2] = -3.;  
    f[3] = -4.;  
    vals.m128_f32[0] = 0.;  
    vals.m128_f32[1] = 1.;  
    vals.m128_f32[2] = 2.;  
    vals.m128_f32[3] = 3.;  
    _mm_stream_ss(&f[3], vals);  
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;  
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;  
}  
```  
  
```Output  
f[0] = -1, f[1] = -2  
f[2] = -3, f[3] = 3  
```  
  
**结束 Microsoft 专用**  

高级微设备，inc.版权所有 2007保留所有权利。 重新生成具有高级微设备，inc.的权限  
  
## <a name="see-also"></a>请参阅  
 [_mm_stream_sd](../intrinsics/mm-stream-sd.md)   
 [_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)   
 [_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)   
 [_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)