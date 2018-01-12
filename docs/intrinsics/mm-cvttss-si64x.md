---
title: "_mm_cvttss_si64x |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mm_cvttss_si64x
dev_langs: C++
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b93426c814378ea3b52dfadd1617b641a7564f16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mmcvttsssi64x"></a>_mm_cvttss_si64x
**Microsoft 专用**  
  
 发出扩展 x64 版本的与截断为 64 位整数的单精度浮点数字转换 (`cvttss2si`) 指令。  
  
## <a name="syntax"></a>语法  
  
```  
__int64 _mm_cvttss_si64x(   
   __m128 value   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `value`  
 `__m128`结构，它包含单精度浮点值。  
  
## <a name="return-value"></a>返回值  
 第一个浮点值转换为 64 位整数的结果。  
  
## <a name="requirements"></a>惠?  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_mm_cvttss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 内部函数不同于`_mm_cvtss_si64x`仅在于准确转换舍去小数。 因为`__m128`结构表示的 XMM 寄存器，生成的指令将数据从的 XMM 寄存器移到系统内存。  
  
 此例程仅可用作内部函数。  
  
## <a name="example"></a>示例  
  
```  
// _mm_cvttss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvttss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] = { 101.5, 200.75,  
                                          300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvttss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
```Output  
101  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [__m128](../cpp/m128.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)