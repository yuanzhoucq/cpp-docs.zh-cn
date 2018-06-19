---
title: __ll_lshift |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
dev_langs:
- C++
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94cf50287c28fe530df939488c4e707d17aede03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327367"
---
# <a name="lllshift"></a>__ll_lshift
**Microsoft 专用**  
  
 将按指定数目的位左移提供的 64 位值。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned __int64 __ll_lshift(  
   unsigned __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `Mask`  
 要左移位的 64 位整数值。  
  
 [in] `nBit`  
 要位移的位数。  
  
## <a name="return-value"></a>返回值  
 掩码移动左`nBit`bits。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__ll_lshift`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 如果编译程序时使用 64 位体系结构和`nBit`大于 63，要位移的位数是`nBit`模 64。 如果在编译程序使用 32 位体系结构和`nBit`大于 31，要位移的位数是`nBit`取模 32。  
  
 `ll`名称中指示这是一个操作上`long long`(`__int64`)。  
  
## <a name="example"></a>示例  
  
```  
// ll_lshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_lshift)  
  
int main()  
{  
   unsigned __int64 Mask = 0x100;  
   int nBit = 8;  
   Mask = __ll_lshift(Mask, nBit);  
   cout << hex << Mask << endl;  
}  
```  
  
## <a name="output"></a>输出  
  
```  
10000  
```  
  
 **请注意**没有左的移位运算的任何无符号的版本。 这是因为`__ll_lshift`已使用一个无符号的输入的参数。 与右移位，不同是值的左移位运算中没有登录依赖性过程，因为结果中的最低有效位始终设置为零而不考虑移动的符号。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)