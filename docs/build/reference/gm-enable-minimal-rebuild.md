---
title: /Gm（启用最小重新生成）
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 7552da4764f009c0848f1d8f420f112be2d1120a
ms.sourcegitcommit: 99437d7da4528ce72cabe6b6a65a9be5dfd090f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2018
ms.locfileid: "51598803"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm（启用最小重新生成）

已否决。 此选项启用最小重新生成，它确定是否需要重新编译包含已更改的 C++ 类定义的 C++ 源文件，该定义存储在头 (.h) 文件中。

## <a name="syntax"></a>语法

```
/Gm
```

## <a name="remarks"></a>备注

**/Gm**已弃用。 它可能不会触发生成某些类型的标头文件更改。 从项目中，可以安全地删除此选项。 若要提高生成时间，我们建议使用预编译标头和增量和并行改为生成选项。 有关不推荐使用的编译器选项的列表，请参阅**已弃用并删除的编译器选项**主题中[按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)。

在首次编译期间，编译器在项目的 .idb 文件中存储源文件和类定义之间的依赖关系信息。 （依赖关系信息表明源文件所依赖的类定义，并且位于哪个.h 文件定义。）后续编译使用存储在.idb 文件中的信息来确定是否源文件需要进行编译，即使它包含已修改的.h 文件。

> [!NOTE]
> 最小重新生成依赖于类定义不会在包含文件之间更改。 类定义对于项目必须是全局的（对于给定类应只有一个定义），因为 .idb 文件中的依赖关系信息是为整个项目创建的。 如果项目中的某个类有多个定义，请禁用最小重新生成。

由于增量链接器不支持通过使用包含在.obj 文件中的 Windows 元数据[/ZW （Windows 运行时编译）](../../build/reference/zw-windows-runtime-compilation.md)选项， **/Gm**选项与不兼容 **/ZW**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **代码生成**属性页。

1. 修改**启用最小重新生成**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)