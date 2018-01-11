---
title: "_mm_extract_si64、 _mm_extracti_si64 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
dev_langs: C++
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cc28de10a2a0d53ee87920d511ea894ad517a79a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mmextractsi64-mmextractisi64"></a>_mm_extract_si64、_mm_extracti_si64
**Microsoft 专用**  
  
 生成`extrq`说明，以指定的 bits 提取其第一个参数的低 64 位。  
  
## <a name="syntax"></a>语法  
  
```  
__m128i _mm_extract_si64(  
   __m128i Source,  
   __m128i Descriptor  
);  
__m128i _mm_extracti_si64(  
   __m128i Source,  
   int Length,  
   int Index  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `Source`  
 使用输入数据中其较低的 64 位一个 128 位字段。  
  
 [in]`Descriptor`  
 描述要提取的位字段一个 128 位字段。  
  
 [in]`Length`  
 一个整数，指定要提取的字段的长度。  
  
 [in]`Index`  
 一个整数，指定要提取的字段的索引  
  
## <a name="return-value"></a>返回值  
 以其最低有效位为单位的提取字段与一个 128 位字段。  
  
## <a name="requirements"></a>惠?  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_mm_extract_si64`|SSE4a|  
|`_mm_extracti_si64`|SSE4a|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 此内部函数生成`extrq`指令以提取从位`Source`。有两个版本的此内部函数：`_mm_extracti_si64`是即时的版本中，和`_mm_extract_si64`是非快速。  每个版本从提取`Source`由其长度和其最低有效位的索引定义的位字段。 长度和索引的值执行求模 64，因此为 63 解释为-1 和 127 之间。 （减少） 了索引和 （减少） 的字段长度的总和大于 64，如果结果不确定。 输入字段长度的零值解释为 64。 如果字段长度和位索引的零个、 bits 63:0`Source`提取。 如果字段长度为零但位索引为非零，则结果是未定义。  
  
 _Mm_extract_si64、 对的调用中`Descriptor`包含 bits 13:8 和 bits 5:0 中提取的数据的字段长度中的索引...  
  
 如果调用`_mm_extracti_si64`使用编译器无法确定为整数常量的自变量编译器生成代码以包的 XMM 寄存器到这些值 (`Descriptor`) 并调用`_mm_extract_si64`。  
  
 若要确定的硬件支持`extrq`指令，请调用`__cpuid`与内部`InfoType=0x80000001`和检查的第 6 位`CPUInfo[2] (ECX)`。 此位将否则如果支持指令，则为 1 和 0。 如果你运行的代码，使用不支持此内部函数硬件`extrq`指令，则结果不可预知。  
  
## <a name="example"></a>示例  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source, descriptor, result1, result2, result3;  
  
int  
main()  
{  
    source.ui64[0] =     0xfedcba9876543210ll;  
    descriptor.ui64[0] = 0x0000000000000b1bll;  
  
    result1.m = _mm_extract_si64 (source.m, descriptor.m);  
    result2.m = _mm_extracti_si64(source.m, 27, 11);  
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
}  
```  
  
```Output  
result1 = 0x30eca86  
result2 = 0x30eca86  
result3 = 0x30eca86  
```  
  
**结束 Microsoft 专用**  
 高级 Micro 设备，inc.版权所有 2007保留所有权利。 重新生成具有高级 Micro 设备，Inc.的权限  
  
## <a name="see-also"></a>请参阅  
 [_mm_insert_si64、 _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)