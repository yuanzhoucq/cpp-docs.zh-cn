---
title: MASM for x64 (ml64.exe)
ms.date: 08/30/2018
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: d9b550313c8e65e47db70dc81519abce7db95da5
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050207"
---
# <a name="masm-for-x64-ml64exe"></a>MASM for x64 (ml64.exe)

Visual Studio 包含 Microsoft 汇编程序（MASM）的32位和64位托管版本，以面向 x64 代码。 命名为 ml64.exe，这是接受 x64 组装器语言的汇编程序。 当你在 Visual Studio 安装过程中选择C++工作负荷时，将安装 MASM 命令行工具。 MASM 工具不可单独下载。 有关如何下载和安装 Visual Studio 副本的说明，请参阅[安装 Visual studio](/visualstudio/install/install-visual-studio)。 如果你不想安装完整的 Visual Studio IDE，但只需要命令行工具，请下载[Visual studio 的生成工具](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)。

若要在命令行上使用 MASM 生成 x64 目标的代码，必须为 x64 目标使用开发人员命令提示，这会设置所需的路径和其他环境变量。 有关如何启动开发人员命令提示的信息，请参阅在[命令行C++上生成 C/代码](../../build/building-on-the-command-line.md)。

有关 ml64.exe 命令行选项的信息，请参阅[ML 和 Ml64.exe 命令行参考](../../assembler/masm/ml-and-ml64-command-line-reference.md)。

X64 或 ARM 目标不支持内联汇编程序或使用 ASM 关键字。 若要将使用内联汇编程序的 x86 代码移植到 x64 或 ARM，可以将代码转换为C++、使用编译器内部函数或创建汇编程序语言源文件。 Microsoft C++编译器支持内部函数，使你能够在接近跨平台的方式的情况下，使用特殊的函数说明，例如，特权、位扫描/测试、互锁等。 有关可用内部函数的信息，请参阅[编译器内部函数](../../intrinsics/compiler-intrinsics.md)。

## <a name="add-an-assembler-language-file-to-a-visual-studio-c-project"></a>将汇编程序语言文件添加到 Visual Studio C++项目

Visual Studio 项目系统支持在C++项目中使用 MASM 生成的汇编程序语言文件。 你可以创建 x64 汇编程序语言源文件，并使用 MASM 将它们生成到对象文件中，该文件支持 x64。 然后，可以将这些对象文件链接到C++为 x64 目标生成的代码。 这是克服 x64 内联汇编程序缺少的一种方法。

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-studio-c-project"></a>向现有的 Visual Studio C++项目添加汇编程序语言文件

1. 在解决方案资源管理器中，选择项目。 在菜单栏上，依次选择 "**项目**"、"**生成自定义**"。

1. 在 " **Visual C++ Build 自定义文件**" 对话框中，选中 " **masm （属性）** " 旁边的复选框。 选择 **"确定"** 以保存所做选择并关闭对话框。

1. 在菜单栏上，依次选择 "**项目**"、"**添加新项**"。

1. 在 "**添加新项**" 对话框中，在中间窗格中选择 **C++ "文件（.cpp）** "。 在 "**名称**编辑控件" 中，输入具有 **.asm**扩展名的新文件名，而不是 .cpp。 选择 "**添加**" 将文件添加到项目中，并关闭对话框。

在添加的 .asm 文件中创建汇编程序语言代码。 生成解决方案时，将调用 MASM 组装器将 .asm 文件组合到对象文件中，然后将该文件链接到项目。 为了更轻松地访问符号，请在C++源代码中将汇编程序函数声明为 `extern "C"`，而不是C++在汇编程序语言源文件中使用名称修饰约定。

## <a name="ml64-specific-directives"></a>ml64.exe 特定指令

可以在面向 x64 的汇编程序语言源代码中使用以下 ml64.exe 特定的指令：

- [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)

- [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)

- [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)

- [.PUSHREG](../../assembler/masm/dot-pushreg.md)

- [.SAVEREG](../../assembler/masm/dot-savereg.md)

- [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)

- [.SETFRAME](../../assembler/masm/dot-setframe.md)

此外， [PROC](../../assembler/masm/proc.md)指令已更新为与 ml64.exe 一起使用。

## <a name="32-bit-address-mode-address-size-override"></a>32位地址模式（地址大小替代）

如果内存操作数包含32位寄存器，则 MASM 发出0x67 地址大小重写。 例如，以下示例将发出地址大小替代：

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM 假设如果32位置换单独显示为内存操作数，则应使用64位寻址。 目前尚不支持此类操作数的32位寻址。

最后，在内存操作数内混合寄存器大小，如下面的代码所示，会生成错误。

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>请参阅

[Microsoft 宏汇编程序参考](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>