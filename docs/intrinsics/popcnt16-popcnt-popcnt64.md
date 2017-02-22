---
title: "__popcnt16, __popcnt, __popcnt64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__popcnt64"
  - "__popcnt"
  - "__popcnt16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "popcnt 指令"
  - "__popcnt16"
  - "__popcnt64"
  - "__popcnt"
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# __popcnt16, __popcnt, __popcnt64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 计数一个 \(种群统计\) 数。 16\-， 32\- 或 64 字节无符号整数。  
  
## 语法  
  
```  
unsigned short __popcnt16(  
   unsigned short value  
);  
unsigned int __popcnt(  
   unsigned int value  
);  
unsigned __int64 __popcnt64(  
   unsigned __int64 value  
);  
```  
  
#### 参数  
 \[in\] `value`  
 我们需要种群统计的 16\-， 32\- 或 64 位无符号整数。  
  
## 返回值  
 一个位于 `value` 参数的位数。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__popcnt16`|高级二进制处理|  
|`__popcnt`|高级二进制处理|  
|`__popcnt64`|高级二进制处理在 64 位模式下。|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 这些内部每个生成`popcnt` 命令。  `popcnt` 命令返回值的大小与其参数的大小。  在 32 位模式下不 64 位通用寄存器，因此不能 64 位 `popcnt`。  
  
 若要确定硬件为 `popcnt`命令支持，调用与 `InfoType=0x00000001` 的 `__cpuid` 内部和校验位 23 `CPUInfo[2] (ECX)`。  此位否则为 1，则命令支持和 0。  如果运行使用在硬件的固有不支持 `popcnt` 命令的代码，结果是不可预知的。  
  
## 示例  
  
```  
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
    usr = __popcnt16(us[i]);  
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __popcnt(ui[i]);  
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
  **\_\_popcnt16 \(0x0\) \= 0**  
 **\_\_popcnt16 \(0xff\) \= 8**  
 **\_\_popcnt16 \(0xffff\) \= 16**  
 **\_\_popcnt \(0x0\) \= 0**  
 **\_\_popcnt \(0xff\) \= 8**  
 **\_\_oopcnt \(0xffff\) \= 16**  
 **\_\_popcnt \(0xffffffff\) \= 32**   
## 特定于 Microsoft 的结尾  
 copyright 2007 年 Advanced Micro 设备，公司着。  保留所有权利。  重现经 Advanced Micro 设备授予，公司。  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)