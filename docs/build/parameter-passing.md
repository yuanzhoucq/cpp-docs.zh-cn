---
title: 参数传递
ms.date: 11/04/2016
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
ms.openlocfilehash: 1b7fb126ab3b140d0ab672067df35c5fc8df926e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648742"
---
# <a name="parameter-passing"></a>参数传递

第四个整数自变量将传入寄存器。 整数值 （按从左到右的顺序） 在 RCX、 RDX、 R8 和 R9 中传递。 参数 5 和更高版本在堆栈上传递。 所有自变量是右对齐，在寄存器中。 这样为了使被调用方可以忽略上面的注册位，如果需要并且可以访问仅注册必要的部分。

浮点和双精度自变量传递到 xmm0-XMM3 （最多 4) 带通常使用该基数槽成为整数插槽 （RCX、 RDX、 R8 和 R9） 被忽略 （参阅示例），反之亦然。

[__m128](../cpp/m128.md)的即时值永远不会传递类型、 数组和字符串，但而是将指针传递到由调用方分配的内存。 结构/联合的大小为 8、 16、 32 或 64 位和 __m64 传递就好像这是相同大小的整数。 这些大小以外的结构/联合作为指针传递给调用方分配的内存。 对于这些聚合类型传递作为指针 (包括\__m128)，调用方分配的临时内存将是 16 字节对齐。

不分配堆栈空间并且不会调用其他函数的内部函数可以使用其他易失寄存器将传递其他寄存器自变量，因为编译器内部函数实现之间紧密绑定。 这是提高性能的更多机会。

被调用方具有转储到其影子空间根据需要将寄存器参数的责任。

下表总结了如何传递参数：

|参数类型|传递方式|
|--------------------|----------------|
|浮点|前 4 个参数-通过 XMM3 XMM0。 其他参数在堆栈上传递。|
|整数|前 4 个参数-RCX，RDX，R8 R9。 其他参数在堆栈上传递。|
|聚合 （8、 16、 32 或 64 位） 和 __m64|前 4 个参数-RCX，RDX，R8 R9。 其他参数在堆栈上传递。|
|聚合 （其他）|通过指针。 4 个参数作为指针在 RCX、 RDX、 R8 和 R9 中传递的第一次|
|__m128|通过指针。 4 个参数作为指针在 RCX、 RDX、 R8 和 R9 中传递的第一次|

## <a name="example-of-argument-passing-1---all-integers"></a>自变量传递 1 的所有整数的示例

```
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

## <a name="example-of-argument-passing-2---all-floats"></a>自变量传递 2-所有浮点数的示例

```
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

## <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>自变量传递 3-混合的整数和浮点数的示例

```
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

## <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>示例中的自变量传递 4-__m64， \__m128，和聚合

```
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="see-also"></a>请参阅

[调用约定](../build/calling-convention.md)