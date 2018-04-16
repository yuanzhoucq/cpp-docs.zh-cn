---
title: "对于 x64 (ml64.exe) MASM |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a42b25b5d86d181bed907a3b437d28f3cbf5e820
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="masm-for-x64-ml64exe"></a>MASM for x64 (ml64.exe)

Visual Studio 包含 32 位和 64 位托管的版 MASM 分发到面向 x64 代码。 名为 ml64.exe，这是接受 x64 汇编程序汇编程序语言。 当你在 Visual Studio 安装期间选择的 c + + 工作负荷时，会安装 MASM 命令行工具。 这些工具不可用作为单独的下载。 若要下载并安装 Visual Studio 的副本，请参阅[https://www.visualstudio.com/](https://www.visualstudio.com/)。 如果您不想安装 Visual Studio IDE，但只需要命令行工具，请参阅**生成 Tools for Visual Studio 2017**选项[Visual Studio 下载](https://www.visualstudio.com/downloads/)页。

若要使用 MASM 构建 x64 代码以在命令行上为目标，你必须使用开发人员命令提示 x64 目标，可将所需的路径和其他环境变量。 有关如何开始开发人员命令提示的信息，请参阅[命令行上的生成 C/c + + 代码](../../build/building-on-the-command-line.md)。

Ml64.exe 命令行选项的信息，请参阅[ML 和 ML64 命令行参考](../../assembler/masm/ml-and-ml64-command-line-reference.md)。  
  
X64 或 ARM 目标不支持内联汇编程序或 ASM 关键字的使用。 端口你 x86 代码，该使用内联汇编程序 x64 或 ARM，你可以将你的代码转换为 c + +、 使用编译器内部函数，或创建源文件的汇编程序语言。 Visual c + + 编译器支持内部函数，以允许你使用特殊函数的说明，示例中，特权，位扫描/测试，互锁，并因此在中, 作为接近尽可能跨平台的方式。 有关可用的内部函数的信息，请参阅[编译器内部函数](../../intrinsics/compiler-intrinsics.md)。  

## <a name="add-an-assembler-language-file-to-a-visual-c-project"></a>将汇编程序语言文件添加到 Visual c + + 项目  
  
Visual Studio 项目系统支持 c + + 项目中使用 MASM 生成汇编程序语言文件。 你可以创建的 x64 汇编程序语言源文件，并通过使用 MASM，完全支持 x64 对象文件到生成它们。 然后，你可以将这些对象文件链接到 c + + 代码生成为 x64 目标。 这是一种解决 x64 缺乏内联汇编程序。  

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-c-project"></a>若要将汇编程序语言文件添加到现有 Visual c + + 项目

1. 选择的项目中**解决方案资源管理器**。 在菜单栏上，选择**项目**，**生成自定义项**。

1. 在**Visual c + + 生成的自定义项文件**对话框框中，选中复选框旁边**masm(.targets,.props)**。 选择**确定**以保存所做选择并关闭对话框。

1. 在菜单栏上，选择**项目**，**添加新项**。 

1. 在**添加新项**对话框中，选择**c + + 文件 (.cpp)**的中心窗格中。 在**名称**编辑控件中，输入新的文件名具有**.asm**而不是.cpp 的扩展。 选择**添加**以将文件添加到你的项目并关闭对话框。

在你添加的.asm 文件中创建汇编程序语言代码。 当生成解决方案时，将调用 MASM 汇编程序.asm 文件装入然后链接到你的项目的对象文件。 若要使符号访问更加轻松，你汇编程序函数声明为`extern "C"`在 c + + 源代码，而不是使用 c + + 名称修饰约定在您汇编程序语言源文件。
  
## <a name="ml64-specific-directives"></a>ml64 特定指令  

在面向 x64 汇编程序语言源代码中，可以使用以下 ml64 特定指令：  
  
-   [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)  
  
-   [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)  
  
-   [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)  
  
-   [.PUSHREG](../../assembler/masm/dot-pushreg.md)  
  
-   [.SAVEREG](../../assembler/masm/dot-savereg.md)  
  
-   [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)  
  
-   [.SETFRAME](../../assembler/masm/dot-setframe.md)  
  
此外， [PROC](../../assembler/masm/proc.md)指令已更新为与 ml64.exe 一起使用。  
  
## <a name="32-bit-address-mode-address-size-override"></a>32 位地址模式 （地址大小或替代）  

如果内存操作数包括 32 位寄存器，MASM 会发出 0x67 地址大小替代。 例如，下面的示例会导致用于发出的地址大小替代：  
  
```MASM  
mov rax, QWORD PTR [ecx]  
mov eax, DWORD PTR [ecx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10d+0100h]  
prefetch [eax]  
movnti rax, QWORD PTR [r8d]  
```  
  
MASM 假定，64 位寻址适用如果 32 位偏移量出现内存操作数作为单独。 目前尚不支持 32 位与此类操作数寻址的方法。  
  
最后，如下面的代码中所示混合寄存器大小中的内存操作数中，将生成错误。  
  
```MASM  
mov eax, DWORD PTR [rcx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10+0100h]  
```  
  
## <a name="see-also"></a>请参阅  

[Microsoft 宏汇编程序参考](../../assembler/masm/microsoft-macro-assembler-reference.md)