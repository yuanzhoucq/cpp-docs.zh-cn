---
title: __asm
ms.date: 10/09/2018
f1_keywords:
- __asm
- _asm
- __asm_cpp
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
ms.openlocfilehash: 14a40bef5b2edba76fc130604414c45eee589bcd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192998"
---
# `__asm`

**Microsoft 专用**

**`__asm`** 关键字调用内联汇编程序，并且可在 c 或 c + + 语句合法的任何位置显示。 它不能单独出现。 它必须后跟一个程序集指令、一组括在大括号中的指令或者至少一对空大括号。 此处的术语 " **`__asm`** 块" 指任何指令或指令组（无论是否在大括号中）。

> [!NOTE]
> Visual C++ 对标准 c + + **`asm`** 关键字的支持仅限于编译器不会在关键字上生成错误的情况。 但是， **`asm`** 块不会生成任何有意义的代码。 使用 **`__asm`** 而不是 **`asm`** 。

## <a name="grammar"></a>语法

*asm-块*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm`***assembly-指令* **`;`**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm {`***程序集指令-列表* **`}`****`;`** <sub>opt</sub>

*程序集指令列表*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-指令* **`;`**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-指令* **`;`***程序集指令-列表* **`;`**<sub>opt</sub>

## <a name="remarks"></a>备注

如果在不使用大括号的情况下使用，则 **`__asm`** 关键字表示此行的其余部分是汇编语言语句。 如果与大括号一起使用，则该关键字表示大括号之间的每一行都是一条汇编语言语句。 为了与早期版本兼容， **`_asm`** 是的同义词 **`__asm`** 。

由于 **`__asm`** 关键字是语句分隔符，因此您可以将程序集指令放在同一行上。

在 Visual Studio 2005 之前，说明

```cpp
__asm int 3
```

在用 **/clr**编译时不会生成本机代码;编译器将指令转换为 CLR 中断指令。

`__asm int 3` 现在将导致为函数生成本机代码。 如果希望函数在代码中引发断点，并要将该函数编译为 MSIL，请使用[__debugbreak](../../intrinsics/debugbreak.md)。

为了与早期版本兼容，为， **`_asm`** **`__asm`** 除非指定编译器选项[/za " \( 禁用语言扩展](../../build/reference/za-ze-disable-language-extensions.md)"，否则将是同义词。

## <a name="example"></a>示例

以下代码片段是 **`__asm`** 括在大括号内的简单块：

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

或者，您可以将放 **`__asm`** 在每个程序集指令前面：

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

由于 **`__asm`** 关键字是语句分隔符，因此您还可以将程序集指令放在同一行上：

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

所有三个示例都生成相同的代码，但第一个样式（ **`__asm`** 用大括号括住块）有一些优点。 大括号清晰地将程序集代码与 C 或 c + + 代码分隔开，并避免不必要地重复 **`__asm`** 关键字。 大括号还可防止二义性。 如果要将 C 或 c + + 语句放在与块相同的行上 **`__asm`** ，则必须将块括在大括号中。 如果没有大括号，编译器将无法告知程序集代码的停止位置以及 C 或 C++ 语句的开始位置。 最后，由于大括号中的文本与普通 MASM 文本具有相同的格式，因此您可以轻松从现有 MASM 源文件剪切并粘贴文本。

不同于 C 和 c + + 中的大括号，封闭块的大括号 **`__asm`** 不会影响变量范围。 还可以嵌套 **`__asm`** 块; 嵌套不影响变量范围。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[关键字](../../cpp/keywords-cpp.md)<br/>
[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>
