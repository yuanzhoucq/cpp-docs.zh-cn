---
title: '/EP（不使用 #line 指令预处理到 stdout）'
ms.date: 11/04/2016
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
ms.openlocfilehash: ad64d39ee6e617556b9210086139c75a246cb63f
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422738"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP（不使用 #line 指令预处理到 stdout）

则预处理 C 和 c + + 源文件，并将预处理过的文件复制到标准输出设备。

## <a name="syntax"></a>语法

```
/EP
```

## <a name="remarks"></a>备注

在过程中，所有预处理器指令则不会执行、 执行宏展开，并会删除注释。 若要保留预处理的输出中的注释，请使用[（预处理期间保留注释） /C](../../build/reference/c-preserve-comments-during-preprocessing.md)选项与 **/EP**。

**/EP**选项将取消编译。 必须重新提交预处理过的文件进行编译。 **/EP**也会从输出文件禁止显示 **/FA**， **/Fa**，并且 **/Fm**选项。 有关详细信息，请参阅[/FA、 /Fa （列表文件）](../../build/reference/fa-fa-listing-file.md)并[/Fm （命名映射文件）](../../build/reference/fm-name-mapfile.md)。

在后续阶段中的处理过程中生成的错误引用的预处理过的文件而不是原始的源文件行号。 如果你想要引用原始源代码文件的行号，使用[/E （预处理到 stdout）](../../build/reference/e-preprocess-to-stdout.md)相反。 **/E**选项将添加`#line`对实现此目的的输出的指令。

要与一起发送预处理的输出`#line`指令，到文件中，使用[/P （预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)选项。

若要使用将预处理的输出发送到 stdout，`#line`指令，使用 **/P**并 **/EP**在一起。

不能使用预编译标头 **/EP**选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**预处理器**属性页。

1. 修改**生成预处理文件**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。

## <a name="example"></a>示例

下面的命令行对文件进行预处理`ADD.C`、 保留注释，并在标准输出设备上显示结果：

```
CL /EP /C ADD.C
```

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
