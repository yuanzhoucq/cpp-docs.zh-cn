---
title: "__ull_rshift |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __ull_rshift
dev_langs: C++
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0d1519ead8d57e350ca0de95ab5db0c9fae14f05
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ullrshift"></a>__ull_rshift
**Microsoft 专用**  
  
 在 x64，右移大量按第二个参数指定的位数向右的第一个参数指定的 64 位值。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned __int64 __ull_rshift(   
   unsigned __int64 mask,    
   int nBit   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `mask`  
 要移动到了右边的 64 位整数值。  
  
 [in] `nBit`  
 要位移，取模上 x86、 32 和模 64 x64 上的位数数。  
  
## <a name="return-value"></a>返回值  
 掩码移动`nBit`bits。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__ull_rshift`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 如果第二个参数大于 31 x86 (63 x64 上) 上，该数字执行取模 32 (x64 上的 64) 来确定要位移的位数数。 `ull`名称中指示`unsigned long long (unsigned __int64)`。  
  
## <a name="example"></a>示例  
  
```  
// ull_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ull_rshift)  
  
int main()  
{  
   unsigned __int64 mask = 0x100;  
   int nBit = 8;  
   mask = __ull_rshift(mask, nBit);  
   cout << hex << mask << endl;  
}  
```  
  
## <a name="output"></a>输出  
  
```  
1  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)