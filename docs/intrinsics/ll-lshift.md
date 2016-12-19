---
title: "__ll_lshift | Microsoft Docs"
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
  - "__ll_lshift_cpp"
  - "__ll_lshift"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ll_lshift 内部函数"
  - "__ll_lshift 内部函数"
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __ll_lshift
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 转换所提供的 64 位值左移按位的指定数目。  
  
## 语法  
  
```  
unsigned __int64 __ll_lshift(  
   unsigned __int64 Mask,  
   int nBit  
);  
```  
  
#### 参数  
 \[in\] `Mask`  
 转换为 64 位整数值左侧。  
  
 \[in\] `nBit`  
 转换的位数。  
  
## 返回值  
 掩码由 `nBit` 位左移。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__ll_lshift`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 如果编译程序使用 64 位体系结构，并 `nBit` 大于 63，转换的位数是 `nBit` 取模 64。  如果编译程序使用 32 位体系结构，并 `nBit` 大于 31，转换的位数是 `nBit` 取模 32。  
  
 在名称中 `ll` 指示这是在 `long long` \(`__int64`\) 的操作。  
  
## 示例  
  
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
  
## Output  
  
```  
10000  
```  
  
 此处**说明**不是左移操作的未签名的版本。  这是因为， `__ll_lshift` 已使用无符号输入参数。  不同右移，，因为在结果的最低有效位始终设置为零无论传输，的值的符号不左移的符号依赖项。  
  
### 特定于 Microsoft 的结尾  
  
## 请参阅  
 [\_\_ll\_rshift](../intrinsics/ll-rshift.md)   
 [\_\_ull\_rshift](../intrinsics/ull-rshift.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)