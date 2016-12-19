---
title: "__emul, __emulu | Microsoft Docs"
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
  - "__emulu_cpp"
  - "__emul"
  - "__emul_cpp"
  - "__emulu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__emul 内部函数"
  - "__emulu 内部函数"
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __emul, __emulu
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 执行相乘该溢出 32 位整数可以保存。  
  
## 语法  
  
```  
__int64 __emul(  
   int a,  
   int b  
);  
unsigned __int64 __emulu(  
   unsigned int a,  
   unsigned int b  
);  
```  
  
#### 参数  
 \[in\] `a`  
 乘法的第一个整型操作数。  
  
 \[in\] `b`  
 乘法的第二个整型操作数。  
  
## 返回值  
 乘法的结果。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__emul`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__emulu`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 `__emul` 采用两个 32 位有符号值并返回相乘的结果作为一个 64 位有符号整数值。  
  
 `__emulu` 采用两个 32 位无符号整数值并返回相乘的结果作为一个 64 位无符号整数值。  
  
## 示例  
  
```  
// emul.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__emul)  
#pragma intrinsic(__emulu)  
  
int main()  
{  
   int a = -268435456;   
   int b = 2;   
  
   __int64 result = __emul(a, b);  
  
   cout << a << " * " << b << " = " << result << endl;  
  
   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295  
   unsigned int ub = 0xF000000;  // Dec value: 251658240  
  
   unsigned __int64 uresult = __emulu(ua, ub);  
  
   cout << ua << " * " << ub << " = " << uresult << endl;  
  
}  
```  
  
## Output  
  
```  
-268435456 * 2 = -536870912  
4294967295 * 251658240 = 1080863910317260800  
```  
  
### 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)