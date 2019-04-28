---
title: x64 调用约定
description: 默认的 x64 ABI 调用约定的详细信息。
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 02bf4719766366049b600b148ad88fc238f4e54e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313606"
---
# <a name="x64-calling-convention"></a>x64 调用约定

本部分介绍的标准过程和一个函数 （调用方） 使用 x64 中进行了另一个函数 （被调用方） 的调用约定的代码。

## <a name="calling-convention-defaults"></a>调用约定默认值

默认的 x64 应用程序二进制接口 (ABI) 使用由四个寄存器快速调用调用约定。 被调用方保存这些寄存器的卷影存储作为调用堆栈上分配空间。 函数调用的参数和用于这些参数的寄存器之间没有一对一的对应关系。 必须通过引用传递任何参数未满 8 个字节，或不是 1、 2、 4 或 8 个字节。 一个自变量从不会分布到多个寄存器。 X87 寄存器堆栈是未使用，并可能由被调用方，但必须考虑易失性整个函数调用。 所有的浮动点完成的操作使用 16 个 XMM 寄存器。 整数自变量将传入 RCX、 RDX、 R8 和 R9 寄存器。 浮点数 XMM0L、 XMM1L、 XMM2L 和 XMM3L 中传递参数。 16 字节参数按引用传递。 中详细描述了参数传递[参数传递](#parameter-passing)。 除了这些寄存器 RAX、 R10、 R11、 XMM4 和 XMM5 被视为易失性。 非易失性的所有其他寄存器。 中详细记录了寄存器用法[注册使用情况](../build/x64-software-conventions.md#register-usage)并[调用方/被调用方保存注册](#callercallee-saved-registers)。

对于原型函数，所有参数都转换为预期的被调用方类型然后才传递。 调用方负责到被调用方，为参数分配空间，并始终必须分配足够的空间来存储四个注册参数，即使被调用方并不需要这么多参数。 此约定可简化支持非原型 C 语言函数和 vararg C /C++函数。 对于 vararg 或 unprototyped 函数，任何浮点值必须在相应的通用寄存器中重复。 后卷影存储调用之前，任何超出前四个参数必须存储在堆栈上。 Vararg 函数详细信息可在[Varargs](#varargs)。 非原型函数的详细信息中[非原型函数](#unprototyped-functions)。

## <a name="alignment"></a>对齐方式

大多数结构对齐到其自然对齐。 主要的例外是堆栈指针并`malloc`或`alloca`内存，以便帮助进行性能 16 个字节对齐。 必须手动完成超过 16 字节的对齐方式，但由于 16 个字节是 XMM 操作的常用对齐大小，此值应适用于大多数代码。 有关结构布局和对齐方式的详细信息，请参阅[类型和存储](../build/x64-software-conventions.md#types-and-storage)。 有关堆栈布局的信息，请参阅[x64 堆栈使用情况](../build/stack-usage.md)。

## <a name="unwindability"></a>Unwindability

叶函数是不会更改任何非易失寄存器的函数。 非叶函数可能更改非易失性 RSP，例如，通过调用一个函数或为本地变量分配附加的堆栈空间。 要进行恢复非易失寄存器，当处理的异常时，必须使用静态数据，介绍如何正确展开的任意指令处函数批注非叶函数。 此数据将被视为*pdata*，或过程数据，又是指*xdata*、 异常处理数据。 Xdata 包含展开的信息，并可以指向其他 pdata 或异常处理程序函数。 Prolog 和 epilog 是高度受限，以便它们可以成为正确 xdata 中所述。 堆栈指针必须是不可构成了 epilog 或序言中，除叶函数中的代码，任何区域中的 16 个字节对齐。 可以只需通过模拟返回时，因此不需要 pdata 和 xdata 展开叶函数。 有关详细信息的函数 prolog 和 epilog 在正确的结构，请参阅[x64 prolog 和 epilog](../build/prolog-and-epilog.md)。 有关异常处理和异常处理和展开 pdata 和 xdata 的详细信息，请参阅[x64 异常处理](../build/exception-handling-x64.md)。

## <a name="parameter-passing"></a>参数传递

第四个整数自变量将传入寄存器。 分别在 RCX、 RDX、 R8 和 R9，从左到右顺序传递的整数值。 参数 5 和更高版本在堆栈上传递。 所有自变量是寄存器的右对齐，在寄存器中，因此被调用方可以忽略高位寄存器并访问只有必要的部分。

任何浮点和双精度自变量中的前四个参数将传入 XMM0-XMM3，具体取决于位置。 整数寄存器 RCX、 RDX、 R8 和 R9 通常使用为这些位置将被忽略，varargs 参数的情况除外。 有关详细信息，请参阅[Varargs](#varargs)。 同样，XMM0-XMM3 对应参数是一个整数或指针类型时，将忽略寄存器。

[__m128](../cpp/m128.md)的即时值永远不会传递类型、 数组和字符串。 相反，对由调用方分配的内存传递的指针。 就像相同大小的整数传递结构和联合的大小为 8、 16、 32 或 64 位和 __m64 类型。 结构或联合的其他大小作为指针传递给调用方分配的内存。 对于传递作为指针，这些聚合类型包括\__m128，调用方分配的临时内存必须是 16 字节对齐。

不分配堆栈空间，并且不调用其他函数的内部函数有时使用其他易失寄存器将附加的寄存器自变量传递。 这种优化由编译器内部函数实现之间的紧密绑定可能。

被调用方负责将寄存器参数转储到必要时其影子空间。

下表总结了如何传递参数：

|参数类型|传递方式|
|--------------------|----------------|
|浮点|前 4 个参数-通过 XMM3 XMM0。 其他参数在堆栈上传递。|
|整数|前 4 个参数-RCX，RDX，R8 R9。 其他参数在堆栈上传递。|
|聚合 （8、 16、 32 或 64 位） 和 __m64|前 4 个参数-RCX，RDX，R8 R9。 其他参数在堆栈上传递。|
|聚合 （其他）|通过指针。 4 个参数作为指针在 RCX、 RDX、 R8 和 R9 中传递的第一次|
|__m128|通过指针。 4 个参数作为指针在 RCX、 RDX、 R8 和 R9 中传递的第一次|

### <a name="example-of-argument-passing-1---all-integers"></a>自变量传递 1 的所有整数的示例

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>自变量传递 2-所有浮点数的示例

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>自变量传递 3-混合的整数和浮点数的示例

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>示例中的自变量传递 4-__m64， \__m128，和聚合

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

如果通过 varargs （例如，省略号参数） 传递的参数，然后正常注册参数传递约定应用，包括将溢出到堆栈的第五个和后续参数。 它是被调用方的职责交给转储采用其地址的参数。 对于浮点值，整数寄存器和浮点寄存器必须包含值，以防被调用方需要采用整数寄存器的值。

## <a name="unprototyped-functions"></a>非原型函数

对于完全保持原型的函数，调用方传递的整数值作为双精度作为整数和浮点值中。 浮点值，对于整数寄存器和浮点寄存器包含 float 值在被调用方需要采用整数寄存器的值的情况下。

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>返回值

可以适合于 64 位的标量返回值返回通过 rax 返回;这包括 __m64 类型。 非标量类型包括浮点数、 双精度数和矢量类型，如[__m128](../cpp/m128.md)， [__m128i](../cpp/m128i.md)， [__m128d](../cpp/m128d.md)以 XMM0 返回。 返回到 RAX 或 XMM0 中的值的未使用位数的状态未定义。

用户定义类型可以从全局函数和静态成员函数通过值返回。 若要值到 RAX 中返回的用户定义的类型，它必须具有 1、 2、 4、 8、 16、 32 或 64 位的长度。 它必须还具有任何用户定义的构造函数、 析构函数或复制赋值运算符;没有私有或受保护的非静态数据成员;任何非静态数据成员的引用类型;没有基类;没有虚函数;并不也满足这些要求没有数据成员。 （这实质上是 C++03 POD 类型的定义。 由于定义已更改 C + + 11 标准中，我们不建议使用`std::is_pod`对于此测试。)否则，调用方有责任分配内存并为返回值传递一个指针作为第一个自变量。 然后，后续自变量将向右移动一个自变量。 相同的指针必须在 RAX 中被调用方返回。

这些示例说明如何为具有指定声明的函数传递参数和返回值：

### <a name="example-of-return-value-1---64-bit-result"></a>返回值 1-64 位的结果示例

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>返回值 2-128 位的结果示例

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>返回值 3-指针的用户类型结果示例

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>返回值 4 的值的用户类型结果示例

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>调用方/被调用方保存的寄存器

注册到 RAX、 RCX、 RDX、 R8，R9、 R10、 R11 被视为易失性并必须考虑销毁函数调用上 (除非否则为安全-进行可证明以通过分析如全程序优化)。

注册 RBX、 RBP、 RDI、 RSI、 RSP、 R12、 R13、 R14，并 R15 被视为非易失性，必须保存并还原函数使用它们。

## <a name="function-pointers"></a>函数指针

函数指针是函数的只需指向相应的标签。 有函数指针的目录 (TOC) 要求没有表。

## <a name="floating-point-support-for-older-code"></a>针对旧代码的浮点支持

MMX 和浮点堆栈寄存器 (MM0-MM7/ST0-ST7) 会保留在上下文切换。 没有这些寄存器显式调用约定。 使用这些寄存器严格禁止在内核模式代码。

## <a name="fpcsr"></a>FpCsr

注册状态还包括 x87 FPU 控制字。 调用约定规定此注册以进行非易失性。

执行程序时的 x87 FPU 控制字寄存器设置为以下的标准值的开头：

| 注册\[位] | 设置 |
|-|-|
| FPCSR\[0:6] | 异常会屏蔽所有 1 的 （屏蔽所有异常） |
| FPCSR\[7] | 保留-0 |
| FPCSR\[8:9] | 精度控制-10B （双精度） |
| FPCSR\[10:11] | 舍入控制-0 （舍入到最近的） |
| FPCSR\[12] | 无穷控制-0 （未使用） |

修改任何 FPCSR 中字段的被调用方必须将它们还原到其调用方返回之前。 此外，已修改任何这些字段的调用方必须将它们还原为其标准值调用被调用方，除非依照约定被调用方需要修改后的值之前。

有两个规则的例外情况有关非易失的控制标志：

1. 在函数中的给定函数有案可稽的目的是修改非易失性 FpCsr 其中标志。

1. 如果已经证明更正这些规则的冲突导致的行为与其中这些规则不会发生冲突，例如，通过全程序分析的程序相同的程序。

## <a name="mxcsr"></a>MxCsr

注册状态还包括 MxCsr。 调用约定将此寄存器划分为易失性的部分而非易失性的部分。 易失性的部分包含的六个状态标志，在 MXCSR\[0:5]，而其余的寄存器，MXCSR\[6:15]，被视为非易失性。

在程序执行的开始处的非易失性的部分设置为以下的标准值：

| 注册\[位] | 设置 |
|-|-|
| MXCSR\[6] | Denormals 是零-0 |
| MXCSR\[7:12] | 异常会屏蔽所有 1 的 （屏蔽所有异常） |
| MXCSR\[13:14] | 舍入控制-0 （舍入到最近的） |
| MXCSR\[15] | 刷新到零掩码下溢-0 （关） |

修改的任何非易失性 MXCSR 中字段的被调用方必须将它们还原到其调用方返回之前。 此外，已修改任何这些字段的调用方必须将它们还原为其标准值调用被调用方，除非依照约定被调用方需要修改后的值之前。

有两个规则的例外情况有关非易失的控制标志：

- 在函数中的给定函数有案可稽的目的是修改非易失性 MxCsr 其中标志。

- 如果已经证明更正这些规则的冲突导致的行为与其中这些规则不会发生冲突，例如，通过全程序分析的程序相同的程序。

除非专门函数的文档中所述，可以跨函数边界的可变部分的 MXCSR 状态不进行任何假设。

## <a name="setjmplongjmp"></a>setjmp/longjmp

当包含 setjmpex.h 或 setjmp.h 时，所有调用[setjmp](../c-runtime-library/reference/setjmp.md)或[longjmp](../c-runtime-library/reference/longjmp.md)导致展开代码调用析构函数和`__finally`调用。  这不同于 x86，包括 setjmp.h 导致`__finally`子句和析构函数不调用。

调用`setjmp`保留当前的堆栈指针、 非易失寄存器和 MxCsr 寄存器。  调用`longjmp`返回到最新`setjmp`调用堆栈指针、 非易失寄存器和 MxCsr 注册时，返回到状态为已保留的最新的站点和重置`setjmp`调用。

## <a name="see-also"></a>请参阅

[x64 软件约定](../build/x64-software-conventions.md)
