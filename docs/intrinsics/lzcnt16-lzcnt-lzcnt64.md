---
title: "__lzcnt16、__lzcnt、__lzcnt64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__lzcnt64"
  - "__lzcnt16"
  - "__lzcnt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__lzcnt 内部函数"
  - "lzcnt 指令"
  - "lzcnt16 内部函数"
  - "lzcnt 内部函数"
  - "__lzcnt16 内部函数"
  - "lzcnt64 内部函数"
  - "__lzcnt64 内部函数"
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# __lzcnt16、__lzcnt、__lzcnt64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 计数前导零的数目 16\-， 32\- 或 64 字节整数。  
  
## 语法  
  
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
  
#### 参数  
 \[in\] `value`  
 浏览的 16\-， 32\- 或 64 位无符号整数带前导零。  
  
## 返回值  
 前导零的位数在 `value` 参数的。  如果 `value` 为零，则返回值是输入操作数 \(16， 32 或 64\) 的范围。  如果最高有效位 `value` 是一个，返回值为零。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__lzcnt16`|高级二进制处理|  
|`__lzcnt`|高级二进制处理|  
|`__lzcnt64`|高级二进制处理在 64 位模式下。|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 这些内部每个生成 `lzcnt` 命令。  `lzcnt` 命令返回值的大小与其参数的大小。  在 32 位模式下不 64 位通用寄存器，因此不能 64 位 `lzcnt`。  
  
 若要确定硬件为`lzcnt` 命令支持调用与 `InfoType=0x80000001` 的 `__cpuid` 内部和校验位 5 `CPUInfo[2] (ECX)`。  此位会为 1，则命令支持和 0。  如果运行使用在硬件的固有不支持`lzcnt` 命令的代码，结果是不可预知的。  
  
## 示例  
  
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
  
  **\_\_lzcnt16 \(0x0\) \= 16**  
 **\_\_lzcnt16 \(0xff\) \= 8**  
 **\_\_lzcnt16 \(0xffff\) \= 0**  
 **\_\_lzcnt \(0x0\) \= 32**  
 **\_\_lzcnt \(0xff\) \= 24**  
 **\_\_lzcnt \(0xffff\) \= 16**  
 **\_\_lzcnt \(0xffffffff\) \= 0**   
## 特定于 Microsoft 的结尾  
 copyright 2007 年 Advanced Micro 设备，公司着。  保留所有权利。  重现经 Advanced Micro 设备授予，公司。  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)