---
title: MASM 的 x64 (ml64.exe) |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe21bcb574c35827b07288dcae16e7ec9e1533d5
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687670"
---
# <a name="masm-for-x64-ml64exe"></a>MASM for x64 (ml64.exe)

Visual Studio 包含 32 位和 64 位托管的版本的 Microsoft Assembler (MASM) 让代码面向 x64。 名为 ml64.exe，这是接受 x64 汇编语言。 在 Visual Studio 安装期间选择的 c + + 工作负载时，会安装 MASM 命令行工具。 MASM 工具不作为单独的下载可用。 有关如何下载和安装 Visual Studio 的副本的说明，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。 如果您不想要安装完整的 Visual Studio IDE，但只需要命令行工具，下载[Visual Studio 2017 生成工具](https://go.microsoft.com/fwlink/p/?linkid=875721)。

若要使用 MASM 构建适用于 x64 的代码在命令行上的目标，则必须为 x64 使用开发人员命令提示设置所需的路径和其他环境变量的目标。 有关如何启动开发人员命令提示的信息，请参阅[命令行上的生成 C/c + + 代码](../../build/building-on-the-command-line.md)。

Ml64.exe 命令行选项的信息，请参阅[ML 和 ML64 命令行参考](../../assembler/masm/ml-and-ml64-command-line-reference.md)。

X64 或 ARM 目标不支持内联汇编程序或 ASM 关键字的使用。 将端口将 x86 代码，该使用内联汇编程序为 x64 或 ARM 时，可以将代码转换为 c + +，使用编译器内部函数，或创建源文件的汇编语言。 Visual c + + 编译器支持内部函数，可以使用特殊函数说明的示例中，特权，位扫描/测试，互锁，并因此在中, 作为接近尽可能跨平台的方式。 有关可用的内部函数的信息，请参阅[编译器内部函数](../../intrinsics/compiler-intrinsics.md)。

## <a name="add-an-assembler-language-file-to-a-visual-c-project"></a>将汇编语言文件添加到 Visual c + + 项目

Visual Studio 项目系统支持在 c + + 项目中使用 MASM 生成的汇编程序语言文件。 您可以创建的 x64 汇编语言源文件，并使用来生成对象文件到 MASM，完全支持 x64。 然后可以将这些对象文件链接到 c + + 代码为 x64 生成的目标。 这是一种方法来克服 x64 缺少内联汇编程序。

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-c-project"></a>若要将汇编语言文件添加到现有的 Visual c + + 项目

1. 在解决方案资源管理器中，选择项目。 在菜单栏上依次选择**项目**，**生成自定义**。

1. 在中**Visual c + + 生成自定义文件**对话框框中，选中复选框旁边**masm(.targets,.props)**。 选择**确定**以保存你的选择并关闭对话框。

1. 在菜单栏上依次选择**项目**，**添加新项**。

1. 在中**添加新项**对话框中，选择**c + + 文件 (.cpp)** 的中心窗格中。 在中**名称**编辑控件中，输入新的文件名的未 **.asm**而不是.cpp 扩展名。 选择**添加**若要将文件添加到你的项目并关闭对话框。

创建在您添加的.asm 文件汇编语言代码。 当在生成解决方案时，MASM 汇编将调用以.asm 文件组装到一个目标文件，然后链接到你的项目。 若要使符号访问更加轻松，声明为汇编函数`extern "C"`在 c + + 源代码，而不是使用 c + + 名称修饰约定汇编语言源文件。

## <a name="ml64-specific-directives"></a>特定于 ml64 的指令

面向 x64 在汇编语言源代码中，可以使用以下特定于 ml64 的指令：

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
