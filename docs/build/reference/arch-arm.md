---
title: /arch (ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: b732a74d5fe223fdaf3b161d4ae92093ab5df407
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807866"
---
# <a name="arch-arm"></a>/arch (ARM)

为 ARM 上的代码生成指定体系结构。 另请参阅[/arch (x86)](arch-x86.md)并[/arch (x64)](arch-x64.md)。

## <a name="syntax"></a>语法

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>自变量

**/arch:ARMv7VE**<br/>
允许使用 ARMv7VE 虚拟化扩展指令。

**/arch:VFPv4**<br/>
允许使用 ARM VFPv4 指令。 如果未指定此选项，则默认为 VFPv3。

## <a name="remarks"></a>备注

`_M_ARM_FP`宏 （适用于仅用于 ARM) 指示 (如果有） **/arch**编译器选项已使用。 有关更多信息，请参见 [Predefined Macros](../../preprocessor/predefined-macros.md)。

当你使用[/clr](clr-common-language-runtime-compilation.md)进行编译， **/arch**对托管函数的代码生成没有影响。 **/arch**仅会影响代码生成的本机函数。

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /arch:ARMv7VE 或 /arch:VFPv4 编译器选项

1. 打开**属性页**项目对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**C/c + +** 文件夹。

1. 选择**命令行**属性页。

1. 在中**其他选项**框中，添加`/arch:ARMv7VE`或`/arch:VFPv4`。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。

## <a name="see-also"></a>请参阅

[/arch（最小 CPU 体系结构）](arch-minimum-cpu-architecture.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
