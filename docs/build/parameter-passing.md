---
title: "参数传递 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0359a6cbbb1f646432b03722cdf4ba3010cffa72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="parameter-passing"></a>参数传递
在寄存器中传递的前四个整数参数。 整数值在 RCX、 RDX、 R8 和 R9 中传递 （按从左到右的顺序）。 自变量 5 和更高版本在堆栈上传递。 所有自变量是右对齐，寄存器中。 这样为了使被调用方可以忽略的寄存器高位，如果需要并且可以访问仅需的寄存器的部分。  
  
 浮点和双精度自变量将传入 XMM0-XMM3 （最多 4) 与通常使用该基数槽正在整数槽 （RCX、 RDX、 R8 和 R9） 忽略 （参阅示例），反之亦然。  
  
 [__m128](../cpp/m128.md)类型、 数组和字符串绝对不传递按即时值但而是将指针传递对由调用方分配的内存。 结构/联合的大小 8、 16、 32 或 64 位和 __m64 传递就像它们是相同大小的整数。 这些大小以外的结构/联合作为指针传递给由调用方分配的内存。 为这些聚合类型作为指针的传递 (包括\__m128)，调用方分配的临时内存将是 16 字节对齐。  
  
 不分配堆栈空间并且不调用其他函数的内部函数可以使用其他易失寄存器将传递其他寄存器自变量，因为编译器和内部函数实现之间紧密的绑定。 这是进一步提高性能的机会。  
  
 被调用方有责任将寄存器参数转储到如果需要其影子空间。  
  
 下表总结了如何传递参数：  
  
|参数类型|如何传递|  
|--------------------|----------------|  
|浮点|第一次 4 参数-通过 XMM3 XMM0。 其他参数在堆栈上传递。|  
|整数|第一次 4 参数-RCX、 RDX、 R8 R9。 其他参数在堆栈上传递。|  
|聚合 （8、 16、 32 或 64 位） 和 __m64|第一次 4 参数-RCX、 RDX、 R8 R9。 其他参数在堆栈上传递。|  
|聚合 （其他）|通过指针传递。 4 个参数作为指针 RCX、 RDX、 R8 和 R9 中传递的第一次|  
|__m128|通过指针传递。 4 个参数作为指针 RCX、 RDX、 R8 和 R9 中传递的第一次|  
  
## <a name="example-of-argument-passing-1---all-integers"></a>自变量传递 1 的所有整数示例  
  
```  
func1(int a, int b, int c, int d, int e);    
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-2---all-floats"></a>自变量传递 2-所有的浮动内容的示例  
  
```  
func2(float a, double b, float c, double d, float e);    
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>自变量传递 3-混合的整数与浮点数的示例  
  
```  
func3(int a, double b, int c, float d);    
// a in RCX, b in XMM1, c in R8, d in XMM3  
```  
  
## <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>自变量传递 4 示例-__m64， \__m128，和聚合  
  
```  
func4(__m64 a, _m128 b, struct c, float d);  
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3  
```  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../build/calling-convention.md)