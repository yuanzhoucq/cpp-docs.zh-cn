---
title: /arch (x64)
ms.date: 11/04/2016
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: c515307ee3a49ef746eea939e90d7aecbd661b95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295274"
---
# <a name="arch-x64"></a>/arch (x64)

在 x64 上为代码生成指定体系结构。 另请参阅[/arch (x86)](arch-x86.md)并[/arch (ARM)](arch-arm.md)。

## <a name="syntax"></a>语法

```
/arch:[AVX|AVX2]
```

## <a name="arguments"></a>自变量

**/arch:AVX**<br/>
启用对 Intel 高级矢量扩展指令的使用。

**/arch:AVX2**<br/>
启用对 Intel 高级矢量扩展 2 指令的使用。

## <a name="remarks"></a>备注

**/arch**仅会影响代码生成的本机函数。 当你使用[/clr](clr-common-language-runtime-compilation.md)进行编译， **/arch**对托管函数的代码生成没有影响。

`__AVX__`预处理器符号定义时 **/arch: avx**指定编译器选项。 `__AVX2__`预处理器符号定义时 **/arch:avx2**指定编译器选项。 有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。 **/Arch:avx2** Visual Studio 2013 Update 2，版本 12.0.34567.1 中引入了选项。

### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /arch:AVX 或 /arch:AVX2 编译器选项

1. 打开**属性页**项目对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性**， **C /C++** 文件夹。

1. 选择**代码生成**属性页。

1. 在中**启用增强指令集**下拉列表框中，选择**高级矢量扩展 (/ /arch: AVX)** 或**高级矢量扩展 2 (/ arch:avx2)**。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。

## <a name="see-also"></a>请参阅

[/arch（最小 CPU 体系结构）](arch-minimum-cpu-architecture.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
