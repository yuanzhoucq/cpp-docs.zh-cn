---
title: _mm_cvtss_si64x | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _mm_cvtss_si64x
dev_langs:
- C++
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 247f7a452d350cc061f323b7889268e766288f4b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x
**Microsoft 专用**  
  
 生成[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]扩展的版本将转换标量单精度浮点数为 64 位整数 (`cvtss2si`) 指令。  
  
## <a name="syntax"></a>语法  
  
```  
__int64 _mm_cvtss_si64x(   
   __m128 value   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `value`  
 `__m128`结构，它包含浮点的值。  
  
## <a name="return-value"></a>返回值  
 64 位整数，为整数的第一个浮点值的转换的结果。  
  
## <a name="requirements"></a>惠?  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_mm_cvtss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 转换为整数的结构值的第一个元素，并将其返回。 在 MXCSR 舍入的控制位用于确定舍入的行为。 舍入模式默认值为舍入到最接近，舍入到偶数如果的小数部分为 0.5。 因为`__m128`结构表示的 XMM 寄存器，此内部操作将从 XMM 寄存器的值，并将其写入系统内存。  
  
 此例程仅可用作内部函数。  
  
## <a name="example"></a>示例  
  
```  
// _mm_cvtss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] =  
                           { 101.25, 200.75, 300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvtss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
```Output  
101  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [__m128d](../cpp/m128d.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)