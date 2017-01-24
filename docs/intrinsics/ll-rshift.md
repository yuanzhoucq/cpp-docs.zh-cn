---
title: "__ll_rshift | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__ll_rshift_cpp"
  - "__ll_rshift"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__ll_rshift 内部函数"
  - "ll_rshift 内部函数"
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __ll_rshift
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 转换第一个参数指定的 64 位值在第二个参数指定许多的位的右侧。  
  
## 语法  
  
```  
__int64 __ll_rshift(  
   __int64 Mask,  
   int nBit  
);  
```  
  
#### 参数  
 \[in\] `Mask`  
 转换为 64 位整数值。  
  
 \[in\] `nBit`  
 位转换的，在 x86 的素模 64 和 32 的数字在 x64 的。  
  
## 返回值  
 `nBit` 转换位掩码。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__ll_rshift`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 如果第二个参数大于 64 在 x64 \(32 在 x86\)，该数字。采用 \(32 在 x86\) 确定的位数的模数值 64 转换。  `ll` 前缀指示这是在 `long long`的操作，另一个名称。 `__int64`， 64 位带符号整型。  
  
## 示例  
  
```  
// ll_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_rshift)  
  
int main()  
{  
   __int64 Mask = - 0x100;  
   int nBit = 4;  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
   Mask = __ll_rshift(Mask, nBit);  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
}  
```  
  
## Output  
  
```  
ffffffffffffff00  
 - 100  
fffffffffffffff0  
 - 10  
```  
  
 请注意，如果使用了 `_ull_rshift` ，该错误地转换的值的如果将为零，因此，该希望的结果不会获取在负值。  
  
### 关闭 Microsoft 特定  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_ll\_lshift](../intrinsics/ll-lshift.md)   
 [\_\_ull\_rshift](../intrinsics/ull-rshift.md)