---
title: __lzcnt16、 __lzcnt、 __lzcnt64 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
dev_langs:
- C++
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86e04182cf673674e1f1ba8c073b624760bc4809
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332788"
---
# <a name="lzcnt16-lzcnt-lzcnt64"></a>__lzcnt16、__lzcnt、__lzcnt64
**Microsoft 专用**  
  
 计数数前导零在 16 位、 32 位或 64 位整数。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned short __lzcnt16(  
   unsigned short value  
);  
unsigned int __lzcnt(  
   unsigned int value  
);  
unsigned __int64 __lzcnt64(  
   unsigned __int64 value  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `value`  
 16 位、 32 或 64 位无符号的整数，以扫描前导零。  
  
## <a name="return-value"></a>返回值  
 前导零位数中的数`value`参数。 如果`value`为零，则返回值是输入操作数 （16、 32 或 64） 的大小。 如果最高有效位`value`为 1，返回值为零。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__lzcnt16`|AMD： 高级的位操作 (ABM)<br /><br /> Intel: Haswell|  
|`__lzcnt`|AMD： 高级的位操作 (ABM)<br /><br /> Intel: Haswell|  
|`__lzcnt64`|AMD： 在 64 位模式下高级位操作 (ABM)。<br /><br /> Intel: Haswell|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 每个这些内部函数生成`lzcnt`指令。  值的大小，`lzcnt`指令返回其自变量的大小相同。  在 32 位模式下有任何 64 位通用寄存器，因此不是 64 位`lzcnt`。  
  
 若要确定的硬件支持`lzcnt`指令调用`__cpuid`与内部`InfoType=0x80000001`和检查的 5 位`CPUInfo[2] (ECX)`。 此位将否则如果支持指令，则为 1 和 0。 如果你运行代码使用此内部函数不支持的硬件上`lzcnt`指令，则结果不可预知。  
  
 不支持的 Intel 处理器上`lzcnt`指令字节编码为执行指令， `bsr` （位扫描反向）。 如果代码可移植性考虑，请考虑使用`_BitScanReverse`内部相反。 有关详细信息，请参阅[_BitScanReverse、 _BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md)。  
  
## <a name="example"></a>示例  
  
```  
// Compile this test with: /EHsc  
#include <iostream>   
#include <intrin.h>   
using namespace std;   
  
int main()   
{  
  unsigned short us[3] = {0, 0xFF, 0xFFFF};  
  unsigned short usr;  
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};  
  unsigned int   uir;  
  
  for (int i=0; i<3; i++) {  
    usr = __lzcnt16(us[i]);  
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __lzcnt(ui[i]);  
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
```Output  
__lzcnt16(0x0) = 16  
__lzcnt16(0xff) = 8  
__lzcnt16(0xffff) = 0  
__lzcnt(0x0) = 32  
__lzcnt(0xff) = 24  
__lzcnt(0xffff) = 16  
__lzcnt(0xffffffff) = 0  
```  
  
**结束 Microsoft 专用**  
 本部分内容是高级 Micro 设备，inc.版权所有 2007保留所有权利。 重新生成具有高级 Micro 设备，Inc.的权限  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)
