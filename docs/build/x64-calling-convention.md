---
title: x64 调用约定
description: 默认 x64 ABI 调用约定的详细信息。
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: caf22172ea5e9c20280bce8e508d72fd30c00c5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335129"
---
# <a name="x64-calling-convention"></a>x64 调用约定

本部分介绍 x64 代码中一个函数（调用方）调用另一个函数（被调用方）的标准流程和约定。

## <a name="calling-convention-defaults"></a>调用约定默认值

默认情况下，x64 应用程序二进制接口 (ABI) 使用四寄存器 fast-call 调用约定。 系统在调用堆栈上分配空间作为影子存储，供被调用方保存这些寄存器。 函数调用的参数与用于这些参数的寄存器之间有着严格的一一对应关系。 任何无法放入 8 字节或者不是 1、2、4 或 8 字节的参数都必须按引用传递。 单个参数永远不会分布在多个寄存器中。 x87 寄存器堆栈闲置不用；被调用方可以使用它，但必须在函数调用中将其视为易失性寄存器。 所有浮点数运算都使用 16 个 XMM 寄存器完成。 整数参数在寄存器 RCX、RDX、R8 和 R9 中传递。 浮点数参数在 XMM0L、XMM1L、XMM2L 和 XMM3L 中传递。 16 字节参数按引用传递。 [参数传递](#parameter-passing)详细介绍了参数传递。 除了这些寄存器，RAX、R10、R11、XMM4 和 XMM5 也被视为易失性寄存器。 所有其他寄存器都是非易失性寄存器。 [寄存器使用](../build/x64-software-conventions.md#register-usage)和[由调用方或被调用方保存的寄存器](#callercallee-saved-registers)详细介绍了寄存器的使用方法。

对于原型函数，在传递参数之前，所有参数都将转换为所需的被调用方类型。 调用方负责为被调用方的参数分配空间，并且必须始终分配足够的空间来存储四个寄存器参数，即使被调用方不使用这么多参数也是如此。 此约定简化了对非原型 C 语言​​函数和 vararg C/C++ 函数的支持。 对于 vararg 或非原型函数，任何浮点值都必须在相应的通用寄存器中重复。 在进行调用之前，必须将除前四个参数外的其他参数存储在影子存储后面的堆栈中。 可以在 [Vararg](#varargs) 中找到 Vararg 函数的详细信息。 [非原型函数](#unprototyped-functions)详细介绍了非原型函数的信息。

## <a name="alignment"></a>对齐方式

大多数结构都按其自然对齐方式对齐。 主要的例外是堆栈指针和 `malloc` 或 `alloca` 内存；为了提高性能，它们对齐到 16 字节。 16 字节以上的对齐必须手动完成，但由于 16 字节是 XMM 运算的常见对齐大小，因此该值应当适用于大多数代码。 有关结构布局和对齐方式的详细信息，请参阅[类型和存储](../build/x64-software-conventions.md#types-and-storage)。 有关堆栈布局的信息，请参阅 [x64 堆栈使用](../build/stack-usage.md)。

## <a name="unwindability"></a>展开能力

叶函数是不更改任何非易失性寄存器的函数。 非叶函数可能会更改非易失性 RSP，例如，通过调用函数或为局部变量分配额外的堆栈空间。 若要在处理异常时恢复非易失性寄存器，必须使用静态数据对非叶函数进行注释，该静态数据描述了如何在任意指令中正确展开函数。 此数据存储为 pdata（过程数据），后者又引用 xdata（异常处理数据）   。 xdata 包含展开信息，并且可以指向其他 pdata 或异常处理程序函数。 Prolog 和 epilog 受到严格限制，因此可以在 xdata 中对其进行正确描述。 堆栈指针必须在任何不属于 epilog 或 prolog 的代码区域中对齐到 16 字节，但在叶函数中除外。 只需模拟返回即可展开叶函数，因此 pdata 和 xdata 不是必需的。 有关函数 prolog 和 epilog 的正确结构的详细信息，请参阅 [x64 prolog 和 epilog](../build/prolog-and-epilog.md)。 有关异常处理以及 pdata 和 xdata 的异常处理和展开的详细信息，请参阅 [x64 异常处理](../build/exception-handling-x64.md)。

## <a name="parameter-passing"></a>参数传递

前四个整数参数在寄存器中传递。 整数值从左到右分别在 RCX、RDX、R8 和 R9 中传递。 第五个及后续参数在堆栈上传递。 所有参数在寄存器中都是向右对齐的，因此被调用方可以忽略寄存器的高位，而只访问所需的寄存器部分。

前四个参数中的所有浮点和双精度参数都在 XMM0 - XMM3（具体视位置而定）中传递。 通常用于这些位置的整数寄存器 RCX、RDX、R8 和 R9 会被忽略，除非传递的是 vararg 参数。 有关详细信息，请参阅 [Vararg](#varargs)。 同样，当相应的参数为整数或指针类型时，将忽略 XMM0 - XMM3 寄存器。

[__m128](../cpp/m128.md) 类型、数组和字符串从不通过即时值传递， 而是将指针传递给调用方分配的内存。 大小为 8、16、32 或 64 位的结构和联合以及 __m64 类型作为相同大小的整数传递。 其他大小的结构或联合作为指针传递给调用方分配的内存。 对于这些作为指针传递的聚合类型，包括 \__m128，调用方分配的临时内存必须对齐 16 字节。

不分配堆栈空间且不调用其他函数的内部函数，有时使用其他易失性寄存器来传递其他寄存器参数。 编译器与内部函数实现之间的紧密绑定使此优化成为可能。

如果需要，被调用方负责将寄存器参数转储到其影子空间中。

下表总结了各种参数的传递方式：

|参数类型|传递方式|
|--------------------|----------------|
|浮点|前 4 个参数 - XMM0 至 XMM3。 其他参数在堆栈上传递。|
|整数|前 4 个参数 - RCX、RDX、R8、R9。 其他参数在堆栈上传递。|
|聚合（8、16、32 或 64 位）和 __m64|前 4 个参数 - RCX、RDX、R8、R9。 其他参数在堆栈上传递。|
|聚合（其他）|通过指针。 前 4 个参数在 RCX、RDX、R8 和 R9 中作为指针传递|
|__m128|通过指针。 前 4 个参数在 RCX、RDX、R8 和 R9 中作为指针传递|

### <a name="example-of-argument-passing-1---all-integers"></a>参数传递示例 1 - 所有整数

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>参数传递示例 2 - 所有浮点数

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>参数传递示例 3 - 整数和浮点数混合

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>参数传递示例 4 -__m64、\__m128 和聚合参数

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

如果通过 vararg（例如，省略号参数）传递参数，则适用常规寄存器参数传递约定，包括将第五个及后续参数溢出到堆栈中。 被调用方负责转储带有其地址的参数。 （仅适用于浮点值）如果被调用方希望在整数寄存器中使用浮点值，则整数寄存器和浮点数寄存器都必须包含该值。

## <a name="unprototyped-functions"></a>非原型函数

对于尚未完全原型化的函数，调用方将整数值作为整数传递，将浮点值作为双精度数传递。 （仅适用于浮点值）如果被调用方希望在整数寄存器中使用浮点值，则整数寄存器和浮点数寄存器都必须包含该值。

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>返回值

可以放入 64 位的标量返回值通过 RAX 返回；这包括 __m64 类型。 非标量类型（包括浮点数、双精度数和矢量类型，如 [__m128](../cpp/m128.md)、[__m128i](../cpp/m128i.md)、[__m128d](../cpp/m128d.md)）返回到 XMM0 中。 返回到 RAX 或 XMM0 中的值的未使用位数的状态未定义。

用户定义类型可以从全局函数和静态成员函数通过值返回。 若要将用户定义类型通过值返回到 RAX 中，其长度必须为 1、2、4、8、16、32 或 64 位。 此外，它必须没有用户定义的构造函数、析构函数或复制赋值运算符；没有私有或受保护的非静态数据成员；没有引用类型的非静态数据成员；没有基类；没有虚函数；没有不满足这些要求的数据成员。 （这实质上是 C++03 POD 类型的定义。 由于 C++11 标准中的定义已更改，我们不建议使用 `std::is_pod` 进行此测试。）否则，调用方有责任分配内存并为返回值传递一个指针作为第一个参数。 然后，后续自变量将向右移动一个自变量。 相同的指针必须在 RAX 中被调用方返回。

这些示例说明如何为具有指定声明的函数传递参数和返回值：

### <a name="example-of-return-value-1---64-bit-result"></a>返回值示例 1 - 64 位结果

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>返回值示例 2 - 128 位结果

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>返回值示例 3 - 通过指针返回的用户类型结果

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>返回值示例 4 - 通过值返回的用户类型结果

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>由调用方或被调用方保存的寄存器

寄存器 RAX、RCX、RDX、R8、R9、R10、R11、XMM0-5 以及 YMM0-15 和 ZMM0-15 的高位被认为具有易失性；进行函数调用时，除非可通过分析（例如全程序优化）来证明其安全性，否则必须将其视为已销毁。 在 AVX512VL 上，ZMM、YMM 和 XMM 寄存器 16-31 具有易失性。

寄存器 RBX、RBP、RDI、RSI、RSP、R12、R13、R14、R15 和 XMM6-15 被认为是非易失性的，必须通过使用它们的函数进行保存和还原。

## <a name="function-pointers"></a>函数指针

函数指针只是指向相应函数标签的指针。 函数指针没有目录 (TOC) 要求。

## <a name="floating-point-support-for-older-code"></a>对旧代码的浮点数支持

进行上下文切换时，会保留 MMX 和浮点数堆栈寄存器 (MM0-MM7/ST0-ST7)。 这些寄存器没有明确的调用约定。 内核模式代码中严禁使用这些寄存器。

## <a name="fpcsr"></a>FpCsr

寄存器状态还包括 x87 FPU 控制字。 调用约定规定该寄存器是非易失性的。

开始执行程序时，x87 FPU 控制字寄存器设置为以下标准值：

| 寄存器\[位] | 设置 |
|-|-|
| FPCSR\[0:6] | 例外屏蔽所有 1（屏蔽所有例外） |
| FPCSR\[7] | 已保留 - 0 |
| FPCSR\[8:9] | 精度控制 - 10B（双精度） |
| FPCSR\[10:11] | 舍入控制 - 0（舍入到最接近的值） |
| FPCSR\[12] | 无穷控制 - 0（未使用） |

修改 FPCSR 中任意字段的被调用方必须先还原这些字段，然后才能返回给其调用方。 此外，在调用被调用方之前，除非按照协议，被调用方需要修改后的值，否则，修改了这些字段的调用方必须将它们还原为标准值。

有关控制标志非易失性的规则有两个例外：

1. 在函数中，所记录的给定函数的用途是修改非易失性 FpCsr 标志。

1. 经分析（例如全程序分析）证实，违反这些规则的程序与不违反这些规则的程序行为一样。

## <a name="mxcsr"></a>MxCsr

寄存器状态还包括 MxCsr。 调用约定将该寄存器分为易失部分和非易失部分。 易失部分由 MXCSR\[0:5] 中的六个状态标志组成，而寄存器的其余部分 (MXCSR\[6:15]) 被视为非易失部分。

开始执行程序时，非易失部分设置为以下标准值：

| 寄存器\[位] | 设置 |
|-|-|
| MXCSR\[6] | 非规格化数为零 - 0 |
| MXCSR\[7:12] | 例外屏蔽所有 1（屏蔽所有例外） |
| MXCSR\[13:14] | 舍入控制 - 0（舍入到最接近的值） |
| MXCSR\[15] | 对于已屏蔽的下溢刷新到零 - 0（关闭） |

修改 MXCSR 中任意非易失字段的被调用方必须先还原这些字段，然后才能返回给其调用方。 此外，在调用被调用方之前，除非按照协议，被调用方需要修改后的值，否则，修改了这些字段的调用方必须将它们还原为标准值。

有关控制标志非易失性的规则有两个例外：

- 在函数中，所记录的给定函数的用途是修改非易失性 MxCsr 标志。

- 经分析（例如全程序分析）证实，违反这些规则的程序与不违反这些规则的程序行为一样。

除非在函数的文档中有特别说明，否则无法假设跨函数边界的 MXCSR 易失部分的状态。

## <a name="setjmplongjmp"></a>setjmp/longjmp

当包含 setjmpex.h 或 setjmp.h 时，对 [setjmp](../c-runtime-library/reference/setjmp.md) 或 [longjmp](../c-runtime-library/reference/longjmp.md) 的所有调用都会导致进行展开，从而调用析构函数和 `__finally` 调用。  这一点与 x86 不同，在 x86 中，包含 setjmp.h 会导致 `__finally` 子句和析构函数不被调用。

调用 `setjmp` 会保留当前堆栈指针、非易失性寄存器和 MxCsr 寄存器。  调用 `longjmp` 会返回到最新的 `setjmp` 调用站点，并将堆栈指针、非易失性寄存器和 MxCsr 寄存器重置回最新 `setjmp` 调用所保留的状态。

## <a name="see-also"></a>请参阅

[x64 软件约定](../build/x64-software-conventions.md)
