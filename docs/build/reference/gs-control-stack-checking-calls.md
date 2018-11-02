---
title: /Gs（控制堆栈检查调用）
ms.date: 10/25/2018
f1_keywords:
- /GS
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
ms.openlocfilehash: 52e203380045c3e23b04950cb241176f10321c2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646456"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs（控制堆栈检查调用）

控制堆栈探测的阈值。

## <a name="syntax"></a>语法

> **/Gs**[*大小*]

## <a name="arguments"></a>自变量

*size*<br/>
（可选）在启动堆栈探测之前局部变量可以占用的字节数。 不允许有空格之间 **/Gs**并*大小*。

## <a name="remarks"></a>备注

一个*堆栈探测*是编译器插入在函数调用的开始处的代码的序列。 堆栈探测启动时，它在内存中良性延伸存储函数的局部变量所需的空间量。 这会导致要以透明方式在必要情况下，该函数的其余部分运行之前附加的堆栈内存中页上的操作系统。

默认情况下，当函数需要的堆栈空间多于一页时，编译器将生成启动堆栈探测的代码。 这相当于一个编译器选项 **/Gs4096** x86、 x64、 ARM，和 ARM64 平台。 此值使应用程序和 Windows 内存管理器可以动态增加运行时提交给程序堆栈的内存量。

> [!NOTE]
> 默认值 **/Gs4096**允许程序堆栈的应用程序的 Windows 运行时适当增长。 我们建议，除非有确切的理由，否则请不要更改默认值。

某些程序（如虚拟设备驱动程序）并不需要这种默认堆栈增长机制。 在这种情况下，堆栈探测不需要，可以停止从生成它们通过设置编译器*大小*大于任何函数需要局部变量存储的值。

**/ Gs0**启动堆栈探测每个函数调用需要存储的本地变量。 这可对性能产生负面影响。

适用于 x64 目标，如果 **/Gs**选项而未指定*大小*参数，它是与相同 **/Gs0**。 如果*大小*参数为 1 到 9，发出警告 D9014，并且效果等同于指定 **/Gs0**。

X86、 ARM，和 ARM64 目标 **/Gs**选项，而不*大小*自变量是与相同 **/Gs4096**。 如果*大小*参数为 1 到 9，发出警告 D9014，并且效果等同于指定 **/Gs4096**。

所有目标*大小*介于 10 和 2147485647 参数指定值处设置的阈值。 一个*大小*2147485648 或更高版本会导致错误 C1049。

您可以使用来启用或关闭堆栈探测[check_stack](../../preprocessor/check-stack.md)指令。 **/Gs**和`check_stack`杂注对标准 C 库例程没有影响; 它们会影响编译函数。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 输入 **/Gs**编译器选项和中的可选大小**其他选项**。 选择**确定**或**应用**以保存所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)