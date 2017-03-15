---
title: "参数传递 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 参数传递
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

前四个整数参数将传入寄存器。  整数值在 RCX、RDX、R8 和 R9 中传递 \(按顺序从左到右\)。  参数五和更高在堆栈上传递。  所有参数是将右侧对齐在注册。  因此，被调用方可以根据需要忽略寄存器中上面的位，并且只访问所需的寄存器部分。  
  
 浮点型和双精度参数传入 XMM0、XMM1、XMM2、XMM3（最大可达 4 个）中，并忽略常用于该基槽的整型槽（RCX、RDX、R8 和 R9）（请参见示例），反之亦然。  
  
 [\_\_m128](../cpp/m128.md) 键入，数组，并字符串传递立即值，但指针相当传递给分配的内存由调用方。  范围 8，16，32 个、64 位和\_\_m64 结构\/联合通过，则相同大小的整数。  结构\/联合除了这些范围外作为指针传递给分配的内存由调用方。  对于这些作为指针（包括 \_\_m128）传递的聚合类型，调用方分配的临时内存将是 16 字节对齐的。  
  
 由于编译器与内部函数实现之间存在紧密的绑定，因此不分配堆栈空间且不调用其他函数的内部函数可以使用其他易失寄存器来传递附加的寄存器参数。  这样便可以进一步改进性能。  
  
 被调用方负责根据需要将寄存器参数转储到它们的阴影空间中。  
  
 下表总结了传递参数的方式：  
  
|参数类型|传递方式|  
|----------|----------|  
|浮点|前 4 个参数传入 XMM0、XMM1、XMM2 和 XMM3 中。  其他参数传递到堆栈中。|  
|Integer|前 4 个参数传入 RCX、RDX、R8 和 R9 中。  其他参数传递到堆栈中。|  
|聚合（8、16、32 或 64 位）和 \_\_m64|前 4 个参数传入 RCX、RDX、R8 和 R9 中。  其他参数传递到堆栈中。|  
|聚合（其他）|通过指针传递。  前 4 个参数作为 RCX、RDX、R8 和 R9 中的指针传递|  
|\_\_m128|通过指针传递。  前 4 个参数作为 RCX、RDX、R8 和 R9 中的指针传递|  
  
## 参数传递示例 1 – 全部都是整型参数  
  
```  
func1(int a, int b, int c, int d, int e);    
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack  
```  
  
## 参数传递示例 2 – 全部都是浮点型参数  
  
```  
func2(float a, double b, float c, double d, float e);    
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack  
```  
  
## 参数传递示例 3 – 既有整型参数又有浮点型参数  
  
```  
func3(int a, double b, int c, float d);    
// a in RCX, b in XMM1, c in R8, d in XMM3  
```  
  
## 参数传递示例 4 –\_\_m64、\_\_m128 和聚合  
  
```  
func4(__m64 a, _m128 b, struct c, float d);  
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3  
```  
  
## 请参阅  
 [调用约定](../build/calling-convention.md)