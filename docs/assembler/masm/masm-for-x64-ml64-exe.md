---
title: MASM for x64 (ml64.exe)
ms.date: 08/30/2018
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 0404bff54a08988a72fcb0a0c075a4446bf90f48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596217"
---
# <a name="masm-for-x64-ml64exe"></a>MASM for x64 (ml64.exe)

Visual Studio 同时包含面向x64 代码的 32 位和 64 位托管版本的 Microsoft Assembler (MASM)。 该汇编程序名为 ml64.exe，接受 x64 汇编语言。 在 Visual Studio 安装期间选择 C++ 工作负载时，会安装 MASM 命令行工具。 MASM 工具不可单独下载。 有关如何下载和安装 Visual Studio 的副本的说明，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。 如果不想安装完整的 Visual Studio IDE，而只需要命令行工具，请下载[Visual Studio 2017 的生成工具](https://go.microsoft.com/fwlink/p/?linkid=875721)。

若要使用 MASM 构建适用于 x64 的代码在命令行上的目标，则必须为 x64 使用开发人员命令提示设置所需的路径和其他环境变量的目标。 有关如何启动开发人员命令提示的信息，请参阅[命令行上的生成 C/c + + 代码](../../build/building-on-the-command-line.md)。

Ml64.exe 命令行选项的信息，请参阅[ML 和 ML64 命令行参考](../../assembler/masm/ml-and-ml64-command-line-reference.md)。

X64 或 ARM 目标不支持使用内联汇编程序或 ASM 关键字。 要将使用内联汇编程序的 x86 代码切换到 x64 或 ARM，可以将代码转换为 C++，使用编译器内部函数，或创建汇编语言的源文件。 Visual C++ 编译器支持内部函数，允许尽可能以跨平台的方式使用特殊函数指令，例如特权指令、位扫描/测试指令、互锁指令等。 有关可用的内部函数的信息，请参阅[编译器内部函数](../../intrinsics/compiler-intrinsics.md)。

## <a name="add-an-assembler-language-file-to-a-visual-c-project"></a>将汇编语言文件添加到 Visual c + + 项目

Visual Studio 项目系统支持在 C + + 项目中使用 MASM 生成汇编程序语言文件。 可以使用 MASM 创建 x64 汇编语言源文件并将其构建为完全支持 x64 的对象文件。 然后可以将这些对象文件链接到专为 x64 目标生成的 C + + 代码。 这是一种可在缺少 x64 内联汇编程序时使用的方法。

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-c-project"></a>将汇编语言文件添加到现有的 Visual c + + 项目

1. 在解决方案资源管理器中，选择项目。 在菜单栏上依次选择**项目**，**生成自定义**。

1. 在中**Visual c + + 生成自定义文件**对话框框中，选中复选框旁边**masm(.targets,.props)**。 选择**确定**以保存你的选择并关闭对话框。

1. 在菜单栏上依次选择**项目**，**添加新项**。

1. 在中**添加新项**对话框中，选择**c + + 文件 (.cpp)** 的中心窗格中。 在中**名称**编辑控件中，输入新的文件名的未 **.asm**而不是.cpp 扩展名。 选择**添加**若要将文件添加到你的项目并关闭对话框。

在添加的 .asm 文件中创建汇编语言代码。 生成解决方案时，会调用 MASM 汇编程序，将该 .asm 文件汇编为一个之后要链接到项目的对象文件。 若要使符号访问更容易，应在 C++ 源代码中将汇编程序函数声明为 `extern "C"`，而不是在汇编语言源文件中使用 C++ 名称修饰约定。

## <a name="ml64-specific-directives"></a>特定于 ml64 的指令

可以在面向 x64 在汇编语言源代码中使用以下特定于 ml64 的指令：

- [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)

- [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)

- [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)

- [.PUSHREG](../../assembler/masm/dot-pushreg.md)

- [.SAVEREG](../../assembler/masm/dot-savereg.md)

- [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)

- [.SETFRAME](../../assembler/masm/dot-setframe.md)

此外， [PROC](../../assembler/masm/proc.md)指令已更新为与 ml64.exe 一起使用。

## <a name="32-bit-address-mode-address-size-override"></a>32 位地址模式 （地址大小重写）

如果内存操作数包括 32 位寄存器，MASM 会发出 0x67 地址大小重写。 例如，下面的示例会导致地址大小替代，以便在发出：

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM 假定如果单独存储操作数为 32 位偏移量出现，64 位寻址预期。 目前尚不支持 32 位寻址使用此类操作数。

最后，混合内存操作数中的寄存器大小，如以下代码所示将生成错误。

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>请参阅

[Microsoft 宏汇编程序参考](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>