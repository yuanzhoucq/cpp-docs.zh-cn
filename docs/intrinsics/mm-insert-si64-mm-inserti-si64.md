---
title: "_mm_insert_si64、 _mm_inserti_si64 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
dev_langs:
- C++
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc85f56660702afe1c05f3626b3b28b0b566dbd5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="mminsertsi64-mminsertisi64"></a>_mm_insert_si64, _mm_inserti_si64
**Microsoft 专用**  
  
 生成`insertq`指令以第二个操作数中的位插入其第一操作数。  
  
## <a name="syntax"></a>语法  
  
```  
__m128i _mm_insert_si64(  
   __m128i Source1,  
   __m128i Source2  
);  
__m128i _mm_inserti_si64(  
   __m128i Source1,  
   __m128i Source2  
   int Length,  
   int Index  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `Source1`  
 输入中的数据字段将插入其较低的 64 位一个 128 位字段。  
  
 [in]  `Source2`  
 与要在其低位中插入的数据一个 128 位字段。  有关`_mm_insert_si64`，还包含以其高位为单位的字段描述符。  
  
 [in]  `Length`  
 一个整数常量，用于指定要插入的字段的长度。  
  
 [in]  `Index`  
 一个整数常量，用于指定将向其插入数据的字段的最低有效位的索引。  
  
## <a name="return-value"></a>返回值  
 其较低的 64 位包含原始的低 64 位的 128 位字段`Source1`与指定的位域替换为的低位`Source2`。 高 64 位的返回值是不确定的。  
  
## <a name="requirements"></a>惠?  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_mm_insert_si64`|SSE4a|  
|`_mm_inserti_si64`|SSE4a|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 此内部函数生成`insertq`指令插入从位`Source2`到`Source1`。 有两个版本的此内部函数： `_mm_inserti_si64`，是即时的版本中，和`_mm_insert_si64`是非快速。  每个版本从 Source2 提取给定长度的位字段，并将其插入 Source1。  提取的位是 Source2 的最低有效位。  这些位将插入字段 Source1 由长度和其最低有效位的索引定义。  长度和索引的值执行求模 64，因此为 63 解释为-1 和 127 之间。 （减少） 位索引和 （减少） 的字段长度的总和大于 64，如果结果不确定。 输入字段长度的零值解释为 64。  如果字段长度和位索引的零个、 bits 63:0`Source2`插入到`Source1`。  如果字段长度为零但位索引为非零，则结果是未定义。  
  
 在 _mm_insert_si64 的调用中，则字段长度包含在 bits 77:72 Source2 和 bits 69:64 中的索引。  
  
 如果调用`_mm_inserti_si64`使用编译器无法确定为整数常量的自变量，编译器将生成代码的 XMM 寄存器到包这些值并调用`_mm_insert_si64`。  
  
 若要确定的硬件支持`insertq`指令调用`__cpuid`与内部`InfoType=0x80000001`和检查的第 6 位`CPUInfo[2] (ECX)`。 此位将否则如果支持指令，则为 1 和 0。 如果你运行代码使用此内部函数不支持的硬件上`insertq`指令，则结果不可预知。  
  
## <a name="example"></a>示例  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source1, source2, source3, result1, result2, result3;  
  
int  
main()  
{  
  
    __int64 mask;  
  
    source1.ui64[0] = 0xffffffffffffffffll;  
    source2.ui64[0] = 0xfedcba9876543210ll;  
    source2.ui64[1] = 0xc10;  
    source3.ui64[0] = source2.ui64[0];  
  
    result1.m = _mm_insert_si64 (source1.m, source2.m);  
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);  
    mask = 0xffff << 12;  
    mask = ~mask;  
    result3.ui64[0] = (source1.ui64[0] & mask) |  
                      ((source2.ui64[0] & 0xffff) << 12);  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
  
}  
```  
  
```Output  
result1 = 0xfffffffff3210fff  
result2 = 0xfffffffff3210fff  
result3 = 0xfffffffff3210fff  
```  
  
**结束 Microsoft 专用**  
 高级 Micro 设备，inc.版权所有 2007保留所有权利。 重新生成具有高级 Micro 设备，Inc.的权限  
  
## <a name="see-also"></a>请参阅  
 [_mm_extract_si64、 _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)