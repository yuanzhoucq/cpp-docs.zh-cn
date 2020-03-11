---
title: x64 调用约定
description: 默认 x64 ABI 调用约定的详细信息。
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 2cad00ac7f2cb5fe086fa262a0f512330997391f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856880"
---
# <a name="x64-calling-convention"></a>x64 调用约定

本部分介绍了一个函数（调用方）用来在 x64 代码中调用另一个函数（被调用方）的标准过程和约定。

## <a name="calling-convention-defaults"></a>调用约定默认值

默认情况下，x64 应用程序二进制接口（ABI）使用四寄存器 fast 调用约定。 空间在调用堆栈上分配为被调用方的卷影存储，用于保存这些寄存器。 函数调用的参数与用于这些参数的寄存器之间存在严格的一一对应关系。 任何不符合8字节的参数，或者不是1、2、4或8字节，都必须按引用传递。 单个参数决不会分布在多个寄存器上。 X87 注册堆栈未使用，可被被调用方使用，但必须在函数调用中将其视为易失性。 所有浮点运算都是使用16个 XMM 寄存器完成的。 在寄存器 RCX、RDX、R8 和 R9 中传递整数参数。 浮点参数传递在 XMM0L、XMM1L、XMM2L 和 XMM3L 中。 16字节参数通过引用传递。 参数传递中对参数传递进行了详细[说明。](#parameter-passing) 除这些寄存器外，还会将 RAX、R10、R11、XMM4 和 XMM5 视为易失性。 所有其他寄存器为非易失性。 注册使用情况的详细信息，请参见[注册使用情况](../build/x64-software-conventions.md#register-usage)和[调用方/被](#callercallee-saved-registers)调用方保存的寄存器。

对于原型函数，在传递之前，所有参数都转换为所需的被调用方类型。 调用方负责为被调用方的参数分配空间，并且必须始终分配足够的空间来存储四个寄存器参数，即使被调用方不接受许多参数也是如此。 此约定简化了对非原型 C 语言函数和 vararg C/C++函数的支持。 对于 vararg 或非原型函数，任何浮点值都必须在相应的通用寄存器中重复。 在调用之前，必须在卷影存储区之后将前四个以外的所有参数存储在堆栈上。 可以在[Varargs](#varargs)中找到 Vararg 函数的详细信息。 [非原型函数](#unprototyped-functions)中详细介绍了非原型函数信息。

## <a name="alignment"></a>Alignment

大多数结构都按其自然对齐方式对齐。 主要的例外是堆栈指针、`malloc` 或 `alloca` 内存，它们的对齐方式为16字节，以便帮助提高性能。 超过16个字节的对齐必须手动完成，但由于16字节是 XMM 操作的常见对齐大小，此值适用于大多数代码。 有关结构布局和对齐方式的详细信息，请参阅[类型和存储](../build/x64-software-conventions.md#types-and-storage)。 有关堆栈布局的信息，请参阅[x64 stack 使用](../build/stack-usage.md)。

## <a name="unwindability"></a>Unwindability

叶函数是不更改任何非易失寄存器的函数。 非叶函数可以更改非易失性 RSP，例如，通过调用函数或为局部变量分配附加堆栈空间。 若要在处理异常时恢复非易失性寄存器，必须使用静态数据批注非叶函数，该静态数据说明如何在任意指令中正确地展开函数。 此数据存储为*pdata*或过程数据，后者又称为*xdata*，即异常处理数据。 Xdata 包含展开信息，可指向其他 pdata 或异常处理程序函数。 Prolog 和 epilogs 受到严格限制，可在 xdata 中正确地进行描述。 堆栈指针必须在任何不属于 epilog 或序言（叶函数除外）的代码区域中与16字节对齐。 只需模拟返回即可展开叶函数，因此 pdata 和 xdata 不是必需的。 有关函数 prolog 和 epilogs 的正确结构的详细信息，请参阅[x64 prolog 和 epilog](../build/prolog-and-epilog.md)。 有关异常处理以及 pdata 和 xdata 的异常处理和展开的详细信息，请参阅[x64 异常处理](../build/exception-handling-x64.md)。

## <a name="parameter-passing"></a>参数传递

在寄存器中传递前四个整数自变量。 整数值在 RCX、RDX、R8 和 R9 中分别按从左到右的顺序传递。 自变量5和更高版本传递到堆栈上。 所有参数在寄存器中右对齐，因此被调用方可以忽略寄存器的上限并仅访问注册部分所需的部分。

前四个参数中的任何浮点和双精度参数均传入 XMM0-XMM3，具体取决于位置。 将忽略通常用于这些位置的 RCX、RDX、R8 和 R9，但在 varargs 参数情况下除外。 有关详细信息，请参阅[Varargs](#varargs)。 同样，如果相应的参数是整数或指针类型，则忽略 XMM0-XMM3 寄存器。

[__m128](../cpp/m128.md)类型、数组和字符串绝不会按即时值传递。 而是将指针传递给调用方分配的内存。 大小为8、16、32或64位、__m64 类型的结构和联合将作为相同大小的整数进行传递。 其他大小的结构或联合将作为指针传递给调用方分配的内存。 对于作为指针传递的这些聚合类型（包括 \__m128），调用方分配的临时内存必须是16字节对齐的。

不分配堆栈空间的内部函数，并且不调用其他函数，有时使用其他易失寄存器传递附加寄存器参数。 编译器与内部函数实现之间的紧密绑定使此优化成为可能。

被调用方负责根据需要将寄存器参数转储到其阴影空间。

下表总结了如何传递参数：

|参数类型|传递方式|
|--------------------|----------------|
|浮点|前4个参数-XMM0 到 XMM3。 传递给堆栈的其他人。|
|Integer|前4个参数-RCX、RDX、R8、R9。 传递给堆栈的其他人。|
|聚合（8、16、32或64位）和 __m64|前4个参数-RCX、RDX、R8、R9。 传递给堆栈的其他人。|
|聚合（其他）|按指针。 在 RCX、RDX、R8 和 R9 中作为指针传递的前4个参数|
|__m128|按指针。 在 RCX、RDX、R8 和 R9 中作为指针传递的前4个参数|

### <a name="example-of-argument-passing-1---all-integers"></a>参数传递 1-所有整数的示例

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>参数传递2的示例-所有浮点型

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>参数传递3个混合整数和浮点数的示例

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>传递 4 __m64、\__m128 和聚合的参数的示例

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

如果通过 varargs （例如，省略号参数）传递参数，则将应用普通寄存器参数传递约定，包括溢出堆栈的第五个参数和后续参数。 被调用方负责转储采用其地址的自变量。 对于浮点值，如果被调用方需要整数寄存器中的值，则整数寄存器和浮点寄存器都必须包含值。

## <a name="unprototyped-functions"></a>非原型函数

对于未完全原型的函数，调用方将整数值作为整数和浮点值传递为双精度。 对于浮点值，整数寄存器和浮点寄存器都包含 float 值，以防被调用方要求整数寄存器中的值。

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>返回值

可容纳64位的标量返回值通过 RAX 返回;这包括 __m64 类型。 非标量类型（包括浮点数、双精度型和矢量类型，如[__m128](../cpp/m128.md)、 [__m128i](../cpp/m128i.md)、 [__m128d](../cpp/m128d.md) ）在 XMM0 中返回。 返回到 RAX 或 XMM0 中的值的未使用位数的状态未定义。

用户定义类型可以从全局函数和静态成员函数通过值返回。 若要按 RAX 返回用户定义类型的值，它的长度必须为1、2、4、8、16、32或64位。 它还必须没有用户定义的构造函数、析构函数或复制赋值运算符;没有私有或受保护的非静态数据成员;没有引用类型的非静态数据成员;无基类;无虚函数;以及不满足这些要求的数据成员。 （这实质上是 C++03 POD 类型的定义。 由于 c + + 11 标准中的定义已更改，因此我们不建议对此测试使用 `std::is_pod`。）否则，调用方假设分配内存并将返回值的指针作为第一个参数传递。 然后，后续自变量将向右移动一个自变量。 相同的指针必须在 RAX 中被调用方返回。

这些示例说明如何为具有指定声明的函数传递参数和返回值：

### <a name="example-of-return-value-1---64-bit-result"></a>返回值 1-64 位结果的示例

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>返回值 2-128 位结果的示例

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>返回值3的示例-按指针的用户类型结果

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>返回值4的示例-按值的用户类型结果

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>调用方/被调用方保存的寄存器

注册 RAX、RCX、RDX、R8、R9、R10、R11、XMM0、YMM0 和 ZMM0-15 的上半部分被视为易失性，在函数调用时必须将其视为已销毁（除非通过分析（如完全程序优化）进行安全可证明）。 在 AVX512VL 上，ZMM、YMM 和 XMM 寄存器16-31 是可变的。

注册 RBX、RBP、RDI.TPL、RSI、RSP、R12、R13、R14、R15 和 XMM6-15 被视为非易失性，且必须通过使用它们的函数进行保存和还原。

## <a name="function-pointers"></a>函数指针
 
函数指针只是指向各自函数的标签的指针。 函数指针没有目录（TOC）要求。

## <a name="floating-point-support-for-older-code"></a>针对旧代码的浮点支持

跨上下文切换保留 MMX 和浮点堆栈寄存器（MM0-MM7/ST0-ST7）。 这些寄存器没有显式调用约定。 在内核模式代码中严格禁止使用这些寄存器。

## <a name="fpcsr"></a>FpCsr

注册状态还包括 x87 FPU 控制字。 调用约定将此寄存器指示为非易失性。

在程序执行开始时，x87 FPU 控制单词 register 设置为以下标准值：

| 注册\[位] | 设置 |
|-|-|
| FPCSR\[0:6] | 异常掩盖全部1个（已屏蔽的所有异常） |
| FPCSR\[7] | 保留-0 |
| FPCSR\[8:9] | 精度控制-非控制（双精度） |
| FPCSR\[10:11] | 舍入控制-0 （舍入到最近） |
| FPCSR\[12] | 无限大控制-0 （未使用） |

修改 FPCSR 中的任何字段的被调用方必须先还原它们，然后才能返回到其调用方。 此外，在调用被调用方之前，已修改了这些字段的调用方必须将它们还原到其标准值，除非被调用方的协议要求修改后的值。

有关控件标志的非波动性的规则有两个例外：

1. 在所记录的给定函数目的是修改非易失性 FpCsr 标志的函数中。

1. 当认定更正这些规则时，会导致与不违反这些规则的程序（例如，通过全程序分析）行为相同的程序。

## <a name="mxcsr"></a>MxCsr

注册状态也包含 MxCsr。 调用约定将此寄存器分为易失性部分和非易失部分。 可变部分包含六个状态标志，在 MXCSR\[0:5] 中，其他寄存器 MXCSR\[6:15] 被视为非易失性。

在程序执行开始时，非易失性部分设置为以下标准值：

| 注册\[位] | 设置 |
|-|-|
| MXCSR\[6] | Denormals 为零-0 |
| MXCSR\[7:12] | 异常掩盖全部1个（已屏蔽的所有异常） |
| MXCSR\[13:14] | 舍入控制-0 （舍入到最近） |
| MXCSR\[15] | 对于被屏蔽的下溢为零（关闭） |

修改 MXCSR 内任何非易失字段的被调用方必须先还原它们，然后才能返回到其调用方。 此外，在调用被调用方之前，已修改了这些字段的调用方必须将它们还原到其标准值，除非被调用方的协议要求修改后的值。

有关控件标志的非波动性的规则有两个例外：

- 在所记录的给定函数目的是修改非易失性 MxCsr 标志的函数中。

- 当认定更正这些规则时，会导致与不违反这些规则的程序（例如，通过全程序分析）行为相同的程序。

除非函数的文档中专门说明，否则不能在函数边界内对 MXCSR 的可变部分的状态进行假设。

## <a name="setjmplongjmp"></a>setjmp/longjmp

如果包括 setjmpex.h 或 setjmp，则所有对[setjmp](../c-runtime-library/reference/setjmp.md)或[longjmp](../c-runtime-library/reference/longjmp.md)的调用都会导致调用析构函数和 `__finally` 调用的展开。  这不同于 x86，其中包括 setjmp 会导致不会调用 `__finally` 子句和析构函数。

对 `setjmp` 的调用会保留当前堆栈指针、非易失性寄存器和 MxCsr 寄存器。  `longjmp` 对的调用将返回到最近的 `setjmp` 调用站点，并重置堆栈指针、非易失性寄存器和 MxCsr 寄存器，并将其重置回最近 `setjmp` 调用保留的状态。

## <a name="see-also"></a>另请参阅

[x64 软件约定](../build/x64-software-conventions.md)
