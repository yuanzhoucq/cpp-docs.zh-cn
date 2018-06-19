---
title: _mm_cvtsi64x_ss |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvtsi64x_ss
dev_langs:
- C++
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb529e8aab204df85de2da0a2fdf4c820964239
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340601"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss
**Microsoft 专用**  
  
 生成[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]扩展的版本为标量单精度浮点值将转换的 64 位整数 (`cvtsi2ss`) 指令。  
  
## <a name="syntax"></a>语法  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `a`  
 `__m128`结构，它包含四个单精度浮点值。  
  
 [in] `b`  
 要转换为浮点值 64 位整数。  
  
## <a name="return-value"></a>返回值  
 `__m128`结构其第一个浮点值转换的结果。 其他三个值均将原样从复制`a`。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_mm_cvtsi64x_ss`|X64|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 `__m128`结构表示的 XMM 寄存器，因此此内部函数，则允许此值`b`从系统内存移动到 XMM 注册。  
  
 此例程仅可用作内部函数。  
  
## <a name="example"></a>示例  
  
```  
// _mm_cvtsi64x_ss.cpp  
// processor: x64  
  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtsi64x_ss)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    a.m128_f32[0] = 0;  
    a.m128_f32[1] = 0;  
    a.m128_f32[2] = 0;  
    a.m128_f32[3] = 0;  
    a = _mm_cvtsi64x_ss(a, b);  
  
    printf_s( "%lf %lf %lf %lf\n",  
              a.m128_f32[0], a.m128_f32[1],   
              a.m128_f32[2], a.m128_f32[3] );  
}  
```  
  
```Output  
54.000000 0.000000 0.000000 0.000000  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [__m128](../cpp/m128.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)