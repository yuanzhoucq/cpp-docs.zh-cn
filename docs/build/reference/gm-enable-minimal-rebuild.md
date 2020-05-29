---
title: /Gm（启用最小重新生成）
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 9b928f3add0a2ec10257bf63fe61a824336c19b8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439644"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm（启用最小重新生成）

已弃用。 此选项启用最小重新生成，它确定是否需要重新编译包含已更改的 C++ 类定义的 C++ 源文件，该定义存储在头 (.h) 文件中。

## <a name="syntax"></a>语法

```
/Gm
```

## <a name="remarks"></a>备注

**/Gm**已弃用。 对于某些类型的标头文件更改，它可能不会触发生成。 你可以从项目安全删除此选项。 为了缩短生成时间，建议改为使用预编译标头和增量和并行生成选项。 有关弃用的编译器选项的列表，请参阅[按类别列出的编译器选项](compiler-options-listed-by-category.md)中的 "**弃用和删除编译器选项**" 部分。

在首次编译期间，编译器在项目的 .idb 文件中存储源文件和类定义之间的依赖关系信息。 （依赖关系信息表明每个源文件所依赖的类定义以及该定义位于哪个 .h 文件中。）后面的编译使用存储在 .idb 文件中的信息确定是否需要编译某个源文件（即使它包含已修改的 .h 文件）。

> [!NOTE]
> 最小重新生成依赖于类定义不会在包含文件之间更改。 类定义对于项目必须是全局的（对于给定类应只有一个定义），因为 .idb 文件中的依赖关系信息是为整个项目创建的。 如果项目中的某个类有多个定义，请禁用最小重新生成。

由于增量链接器不支持 .obj 文件中包含的 Windows 元数据（通过使用[/ZW （Windows 运行时编译）选项）](zw-windows-runtime-compilation.md) ， **/Gm**选项与 **/ZW**不兼容。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" > " **C/C++**  > **代码生成**" 属性页。

1. 修改 "**启用最小重新生成**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
