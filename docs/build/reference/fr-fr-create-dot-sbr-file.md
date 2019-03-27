---
title: /FR、/Fr（创建 .Sbr 文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
ms.openlocfilehash: 73642baba77a62cac531ae7b2842ec9953b338ec
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508697"
---
# <a name="fr-fr-create-sbr-file"></a>/FR、/Fr（创建 .Sbr 文件）

创建 .sbr 文件。

## <a name="syntax"></a>语法

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>备注

> [!WARNING]
> 虽然安装 Visual Studio 时仍会安装 BSCMAKE，但 IDE 将不再使用它。 从 Visual Studio 2008 起，浏览信息和符号信息自动存储在解决方案文件夹的 SQL Server .sdf 文件中。

在生成过程中，Microsoft 浏览信息文件维护实用工具 (BSCMAKE) 将使用这些文件来创建 .BSC 文件，用于显示浏览信息。

**/FR** 可创建具有完整符号信息的 .sbr 文件。

**/Fr** 将创建不含任何局部变量信息的 .sbr 文件。

如果不指定 `filename`，则该 .sbr 文件将获取与源文件相同的基名称。

**/Fr** 已弃用；请改用 **/FR** 。 有关详细信息，请参阅 [Compiler Options Listed by Category](compiler-options-listed-by-category.md)中的“已弃用并删除的编译器选项”。

> [!NOTE]
>  请勿更改 .sbr 扩展名。 BSCMAKE 要求中间文件具有此扩展名。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 在导航窗格中，选择“C/C++” 、“浏览信息”  属性页。

1. 修改“浏览信息文件”  或“启用浏览信息”  属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>。

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](output-file-f-options.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[指定路径名](specifying-the-pathname.md)
