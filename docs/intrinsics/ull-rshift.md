---
title: "__ull_rshift | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__ull_rshift"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ull_rshift 内部函数"
  - "__ull_rshift 内部函数"
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __ull_rshift
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 在 x64， shift 第一个参数指定的 64 位值在第二个参数指定许多的位的右侧。  
  
## 语法  
  
```  
unsigned __int64 __ull_rshift(   
   unsigned __int64 mask,    
   int nBit   
);  
```  
  
#### 参数  
 \[in\] `mask`  
 转换为 64 位整数值。  
  
 \[in\] `nBit`  
 位转换的，在 x64 的素模 32 和 64 的数字在 x86 的。  
  
## 返回值  
 `nBit` 转换位掩码。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__ull_rshift`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 如果第二个参数大于 31 on x86 \(63 在 x64\)，该数字。采用 \(64 在 x64\) 确定的位数的模数值 32 转换。  在名称中 `ull` 指示 `unsigned long long (unsigned __int64)`。  
  
## 示例  
  
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
  
## Output  
  
```  
1  
```  
  
### 特定于 Microsoft 的结尾  
  
## 请参阅  
 [\_\_ll\_lshift](../intrinsics/ll-lshift.md)   
 [\_\_ll\_rshift](../intrinsics/ll-rshift.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)