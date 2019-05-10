---
title: '/FU（命名强制 #using 文件）'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
ms.openlocfilehash: c47a45208ac5b5c7e0000516ed114c008feda7ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292284"
---
# <a name="fu-name-forced-using-file"></a>/FU（命名强制 #using 文件）

可以使用作为传递到的文件名称的替代方法的编译器选项[#using 指令](../../preprocessor/hash-using-directive-cpp.md)源代码中。

## <a name="syntax"></a>语法

> **/FU** *file*

## <a name="arguments"></a>自变量

文件<br/>
指定要在此编译中引用的元数据文件。

## <a name="remarks"></a>备注

/FU 开关只采用一个文件名。 若要指定多个文件，请对每个文件使用 /FU。

如果使用的C++/CLI 并引用元数据来使用[友元程序集](../../dotnet/friend-assemblies-cpp.md)功能，不能使用 **/FU**。 你必须将 `#using` 与 `[as friend]` 特性一起使用，才能在代码中引用元数据。 在 Visual 中不支持友元程序集C++组件扩展C++/CX。

有关如何创建程序集或模块的公共语言运行时 (CLR) 的信息，请参阅[/clr （公共语言运行时编译）](clr-common-language-runtime-compilation.md)。 有关如何生成C++/CX，请参阅[构建应用程序和库](../../cppcx/building-apps-and-libraries-c-cx.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C /C++** > **高级**属性页。

1. 修改**强制 #using**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>。

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](output-file-f-options.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
