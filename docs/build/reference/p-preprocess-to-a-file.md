---
title: /P（预处理到文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
ms.openlocfilehash: 5e1280b404668cebb64afa5a810d769a97bdbf85
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418056"
---
# <a name="p-preprocess-to-a-file"></a>/P（预处理到文件）

预处理 C 和 c + + 源文件并将预处理的输出写入到一个文件。

## <a name="syntax"></a>语法

```
/P
```

## <a name="remarks"></a>备注

该文件具有相同的基名称作为源文件和.i 扩展。 在过程中，所有预处理器指令则不会执行、 执行宏展开，并会删除注释。 若要保留预处理的输出中的注释，请使用[（预处理期间保留注释） /C](../../build/reference/c-preserve-comments-during-preprocessing.md)选项和 **/P**。

**/ P**添加`#line`到输出中，在开头和结尾的每个包含的文件以及进行条件编译的预处理器指令中删除的行的周围的指令。 这些指令重新编号预处理过的文件的行。 结果是，在后续阶段中的处理过程中生成的错误引用的原始源文件而不是预处理过的文件中的行的行号。 若要取消的生成`#line`指令，使用[/EP （不预处理到 stdout #line 指令)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ，以及 **/P**。

**/P**选项将取消编译。 它不会生成.obj 文件中，即使您使用[/Fo （对象文件名）](../../build/reference/fo-object-file-name.md)。 必须重新提交预处理过的文件进行编译。 **/ P**也会从输出文件禁止显示 **/FA**， **/Fa**，并且 **/Fm**选项。 有关详细信息，请参阅[/FA、 /Fa （列表文件）](../../build/reference/fa-fa-listing-file.md)并[/Fm （命名映射文件）](../../build/reference/fm-name-mapfile.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**预处理器**属性页。

1. 修改**生成预处理文件**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。

## <a name="example"></a>示例

下面的命令行对进行预处理`ADD.C`，保留注释，添加`#line`指令，并将结果写入到一个文件， `ADD.I`:

```
CL /P /C ADD.C
```

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[/Fi（预处理输出文件名）](../../build/reference/fi-preprocess-output-file-name.md)
