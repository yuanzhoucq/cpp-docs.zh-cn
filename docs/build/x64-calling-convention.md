---
title: x64 调用约定
description: 默认 x64 ABI 调用约定的详细信息。
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: caf22172ea5e9c20280bce8e508d72fd30c00c5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335129"
---
# <a name="x64-calling-convention"></a>x64 调用约定

本节介绍一个函数（调用方）用于在 x64 代码中调用另一个函数（被叫方）的标准进程和约定。

## <a name="calling-convention-defaults"></a>调用约定默认值

默认情况下，x64 应用程序二进制接口 （ABI） 使用四寄存器快速呼叫调用约定。 在调用堆栈上分配空间作为阴影存储，供被调用方保存这些寄存器。 函数调用的参数与用于这些参数的寄存器之间有严格的一对一对应关系。 任何不适合 8 个字节或不是 1、2、4 或 8 字节的参数都必须通过引用传递。 单个参数永远不会跨多个寄存器分布。 x87 寄存器堆栈未使用，可能被被调用者使用，但必须在函数调用之间被视为易失性。 所有浮点操作都使用 16 XMM 寄存器完成。 整数参数在寄存器 RCX、RDX、R8 和 R9 中传递。 浮点参数在 XMM0L、XMM1L、XMM2L 和 XMM3L 中传递。 16 字节参数通过引用传递。 参数传递在[参数传递](#parameter-passing)中进行了详细描述。 除了这些寄存器外，RAX、R10、R11、XMM4 和 XMM5 被认为是易挥发性的。 所有其他寄存器都是非易失性的。 寄存器使用情况在[注册使用情况](../build/x64-software-conventions.md#register-usage)和[呼叫者/被叫者保存的寄存器](#callercallee-saved-registers)中详细记录。

对于原型函数，所有参数在传递之前都将转换为预期的被叫者类型。 调用方负责为被调用方分配参数空间，并且必须始终分配足够的空间来存储四个寄存器参数，即使被调用方不采用那么多参数也是如此。 此约定简化了对未原型 C 语言函数和 vararg C/C++ 函数的支持。 对于 vararg 或未原型函数，必须在相应的通用寄存器中复制任何浮点值。 前四个以外的任何参数都必须在调用之前在卷影存储之后存储在堆栈上。 瓦拉格功能细节可以在[瓦拉格找到](#varargs)。 未原型函数信息在[未原型函数](#unprototyped-functions)中详细说明。

## <a name="alignment"></a>Alignment

大多数结构与其自然对齐。 主要例外是堆栈指针和`malloc`或`alloca`内存，它们对齐为 16 个字节，以帮助性能。 超过 16 个字节的对齐必须手动完成，但由于 16 个字节是 XMM 操作的常见对齐大小，此值应适用于大多数代码。 有关结构布局和对齐的详细信息，请参阅[类型和存储](../build/x64-software-conventions.md#types-and-storage)。 有关堆栈布局的信息，请参阅[x64 堆栈用法](../build/stack-usage.md)。

## <a name="unwindability"></a>可展开性

叶函数是不更改任何非易失寄存器的函数。 非叶函数可能会更改非易失性 RSP，例如，通过调用函数或为局部变量分配额外的堆栈空间。 为了在处理异常时恢复非易失寄存器，必须使用静态数据来说明非叶函数，这些数据描述如何在任意指令下正确展开函数。 此数据存储为*pdata*， 或过程数据， 反过来又指*xdata，* 异常处理数据. xdata 包含展开信息，并可以指向其他 pdata 或异常处理程序函数。 Prologs 和表皮受到高度限制，因此可以在 xdata 中正确描述它们。 堆栈指针必须与不属于表征或 prolog 的任何代码区域中的 16 个字节对齐，但叶函数中除外。 叶函数只需模拟返回即可解覆，因此不需要 pdata 和 xdata。 有关函数序言和表征的正确结构的详细信息，请参阅[x64 prolog 和 epilog](../build/prolog-and-epilog.md)。 有关异常处理以及 pdata 和 xdata 的异常处理和展开的详细信息，请参阅[x64 异常处理](../build/exception-handling-x64.md)。

## <a name="parameter-passing"></a>参数传递

前四个整数参数在寄存器中传递。 整数值分别以 RCX、RDX、R8 和 R9 的从左到右顺序传递。 参数 5 和更高版本在堆栈上传递。 所有参数在寄存器中都是正确的，因此被调用人可以忽略寄存器的上位，并且只访问寄存器所需的部分。

前四个参数中的任何浮点和双精度参数都以 XMM0 - XMM3 传递，具体取决于位置。 通常用于这些位置的整数寄存器 RCX、RDX、R8 和 R9 将被忽略，但 varargs 参数除外。 有关详细信息，请参阅[Varargs](#varargs)。 同样，当相应的参数是整数或指针类型时，将忽略 XMM0 - XMM3 寄存器。

[__m128](../cpp/m128.md)类型、数组和字符串永远不会通过即时值传递。 相反，指针将传递给调用方分配的内存。 大小 8、16、32 或 64 位的结构并结合，以及__m64类型，传递它们就像大小相同的整数一样传递。 其他大小的结构或联合作为指针传递给调用方分配的内存。 对于作为指针传递的聚合类型（包括\__m128，调用方分配的临时内存必须对齐 16 字节。

不分配堆栈空间且不调用其他函数的内在函数，有时使用其他易失寄存器来传递其他寄存器参数。 编译器和内部函数实现之间的紧密绑定使得这种优化成为可能。

如果需要，被调用人负责将寄存器参数转储到其阴影空间中。

下表总结了如何传递参数：

|参数类型|如何通过|
|--------------------|----------------|
|浮点|前 4 个参数 - XMM0 到 XMM3。 其他人在堆栈上传递。|
|Integer|前 4 个参数 - RCX、RDX、R8、R9。 其他人在堆栈上传递。|
|聚合（8、16、32 或 64 位）和__m64|前 4 个参数 - RCX、RDX、R8、R9。 其他人在堆栈上传递。|
|聚合（其他）|按指针。 前 4 个参数在 RCX、RDX、R8 和 R9 中作为指针传递|
|__m128|按指针。 前 4 个参数在 RCX、RDX、R8 和 R9 中作为指针传递|

### <a name="example-of-argument-passing-1---all-integers"></a>参数传递 1 的示例 - 所有整数

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>参数传递 2 的示例 - 所有浮点

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>参数传递 3 - 混合 int 和 floats 的示例

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>通过 4-__m64、_m128\_和聚合的参数示例

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

如果参数通过 varargs 传递（例如，省略号参数），则应用正常的寄存器参数传递约定，包括将第五个和后续参数溢出到堆栈中。 被调用人有责任转储具有其地址的参数。 对于仅浮点值，整数寄存器和浮点寄存器都必须包含该值，以防被叫者期望在整数寄存器中的值。

## <a name="unprototyped-functions"></a>未原型函数

对于未完全原型的函数，调用方将整数值作为整数和浮点值作为双精度传递。 对于仅浮点值，整数寄存器和浮点寄存器都包含浮点值，以防被叫者期望在整数寄存器中的值。

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>返回值

可放入 64 位的标量返回值通过 RAX 返回;这包括__m64类型。 非标量类型（包括浮点、双精度值和矢量类型（如[__m128、__m128i、__m128d）](../cpp/m128i.md)在 XMM0 中返回。 [__m128](../cpp/m128.md) [__m128d](../cpp/m128d.md) 返回到 RAX 或 XMM0 中的值的未使用位数的状态未定义。

用户定义类型可以从全局函数和静态成员函数通过值返回。 要按 RAX 中的值返回用户定义的类型，它必须具有 1、2、4、8、16、32 或 64 位的长度。 它还必须没有用户定义的构造函数、析构函数或复制赋值运算符;没有私有或受保护的非静态数据成员;没有引用类型的非静态数据成员;无基类;无虚拟函数;并且没有也不符合这些要求的数据成员。 （这实质上是 C++03 POD 类型的定义。 由于定义在 C++11 标准中已更改，因此我们不建议使用此`std::is_pod`测试。否则，调用方承担分配内存和传递返回值的指针作为第一个参数的责任。 然后，后续自变量将向右移动一个自变量。 相同的指针必须在 RAX 中被调用方返回。

这些示例说明如何为具有指定声明的函数传递参数和返回值：

### <a name="example-of-return-value-1---64-bit-result"></a>返回值 1 - 64 位结果的示例

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>返回值 2 - 128 位结果的示例

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>返回值 3 - 用户类型结果（指针）的示例

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>返回值 4 示例 - 按值计算的用户类型结果

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>呼叫者/被叫者保存的寄存器

寄存器 RAX、RCX、RDX、R8、R9、R10、R11、XMM0-5 以及 YMM0-15 和 ZMM0-15 的上部被视为易失性，必须在函数调用时被视为销毁（除非通过分析（如整个程序优化）进行安全证明）。 在 AVX512VL 上，ZMM、YMM 和 XMM 寄存器 16-31 是不稳定的。

寄存器 RBX、RBP、RDI、RSI、RSP、R12、R13、R14、R15 和 XMM6-15 被视为非易失性寄存器，必须通过使用它们的函数进行保存和恢复。

## <a name="function-pointers"></a>函数指针

函数指针只是指向相应函数标签的指针。 函数指针没有目录 （TOC） 要求。

## <a name="floating-point-support-for-older-code"></a>对旧代码的浮点支持

MMX 和浮点堆栈寄存器 （MM0-MM7/ST0-ST7） 跨上下文开关保留。 这些寄存器没有显式调用约定。 在内核模式代码中严禁使用这些寄存器。

## <a name="fpcsr"></a>FpCsr

寄存器状态还包括 x87 FPU 控制字。 调用约定指示此寄存器是非易失性的。

x87 FPU 控制字寄存器在程序执行开始时设置为以下标准值：

| 注册\[位* | 设置 |
|-|-|
| FPCSR\[0：6] | 异常屏蔽所有 1（所有例外都已屏蔽） |
| FPCSR\[7* | 保留 - 0 |
| FPCSR\[8：9] | 精密控制 - 10B（双精度） |
| FPCSR\[10：11* | 舍入控制 - 0（舍入到最近） |
| FPCSR\[12* | 无限控制 - 0（未使用） |

修改 FPCSR 中任何字段的被调用方必须先还原这些字段，然后才能返回到其调用方。 此外，已修改这些字段中的任何一个的调用方必须在调用被叫方之前将它们还原到其标准值，除非通过协议被叫方希望修改值。

关于控制标志的非波动性的规则有两个例外：

1. 在给定函数的记录用途是修改非易失性 FpCsr 标志的函数中。

1. 当证明违反这些规则会导致程序的行为与程序的行为相同时，例如，通过整个程序分析，这些程序的行为与程序相同。

## <a name="mxcsr"></a>MxCsr

寄存器状态还包括 MxCsr。 调用约定将此寄存器划分为易失性部分和非易失性部分。 易失性部分由 MXCSR\[0：5+ 中的六个状态标志组成，而寄存器的其余部分 MXCSR\[6：15] 则被视为非易失性标志。

在程序执行开始时，非易失性部分设置为以下标准值：

| 注册\[位* | 设置 |
|-|-|
| MXCSR\[6* | 非正常值为零 - 0 |
| MXCSR\[7：12] | 异常屏蔽所有 1（所有例外都已屏蔽） |
| MXCSR\[13：14* | 舍入控制 - 0（舍入到最近） |
| MXCSR\[15* | 为屏蔽将刷新为零 - 0 （关闭） |

修改 MXCSR 中任何非易失性字段的被调用方必须先还原这些字段，然后才能返回到其调用方。 此外，已修改这些字段中的任何一个的调用方必须在调用被叫方之前将它们还原到其标准值，除非通过协议被叫方希望修改值。

关于控制标志的非波动性的规则有两个例外：

- 在给定函数的记录用途是修改非易失性 MxCsr 标志的函数中。

- 当证明违反这些规则会导致程序的行为与程序的行为相同时，例如，通过整个程序分析，这些程序的行为与程序相同。

除非函数的文档中具体描述，否则无法对跨函数边界的 MXCSR 易失性部分的状态做出任何假设。

## <a name="setjmplongjmp"></a>塞特詹普/隆詹姆

当您包括 setjmpex.h 或 setjmp.h 时，所有对[setjmp](../c-runtime-library/reference/setjmp.md)或[longjmp](../c-runtime-library/reference/longjmp.md)的调用都会导致`__finally`展开，从而调用析构函数和调用。  这与 x86 不同，其中包含 setjmp.h`__finally`会导致不调用子句和析构函数。

保留`setjmp`当前堆栈指针、非易失寄存器和 MxCsr 寄存器的调用。  调用以`longjmp`返回到最新的`setjmp`调用站点并重置堆栈指针、非易失寄存器和 MxCsr 寄存器，返回到最近`setjmp`调用保留的状态。

## <a name="see-also"></a>另请参阅

[x64 软件约定](../build/x64-software-conventions.md)
