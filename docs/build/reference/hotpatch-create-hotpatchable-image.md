---
title: /hotpatch（创建可热修补的映像）
ms.date: 11/12/2018
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
ms.openlocfilehash: 8830b26b8fdfc3db2aa5fe31a52e6226fd554946
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807476"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch（创建可热修补的映像）

准备映像以进行热修补。

## <a name="syntax"></a>语法

```
/hotpatch
```

## <a name="remarks"></a>备注

当 **/hotpatch**使用在编译时，编译器可确保每个函数的第一个指令为至少两个字节，这是进行热修补所要求。

若要完成使用后使映像可以热修补，准备 **/hotpatch**进行编译，必须使用[/FUNCTIONPADMIN （创建可热修补映像）](functionpadmin-create-hotpatchable-image.md)链接。 编译和链接映像使用的 cl.exe，一次调用时 **/hotpatch**意味着 **/functionpadmin**。

因为说明始终是两个字节或 ARM 体系结构，更大并且 x64 编译总是被视为如同 **/hotpatch**已指定，无需指定 **/hotpatch**时编译为这些目标;但是，你必须仍使用链接 **/functionpadmin**若要为其创建可热修补映像。 **/Hotpatch**编译器选项仅影响 x86 编译。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**C/c + +** 文件夹。

1. 选择**命令行**属性页。

1. 添加到编译器选项**其他选项**框。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
