---
title: /E（预处理到 stdout）
ms.date: 11/04/2016
f1_keywords:
- /e
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
ms.openlocfilehash: 892203d300c07711d06cff602128ec6e9ceb351c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504568"
---
# <a name="e-preprocess-to-stdout"></a>/E（预处理到 stdout）

则预处理 C 和 c + + 源文件，并将预处理过的文件复制到标准输出设备。

## <a name="syntax"></a>语法

```
/E
```

## <a name="remarks"></a>备注

在此过程中，所有预处理器指令则不会执行、 执行宏展开，并会删除注释。 若要保留预处理的输出中的注释，请使用[/C （预处理期间保留注释）](../../build/reference/c-preserve-comments-during-preprocessing.md)编译器选项。

**/E**添加`#line`对的开头和结尾的每个包含的文件以及由预处理器指令进行条件编译删除的行的周围的输出的指令。 这些指令重新编号预处理过的文件的行。 结果是，在后续阶段中的处理过程中生成的错误引用的原始源文件而不是预处理过的文件中的行的行号。

**/E**选项将取消编译。 必须重新提交预处理过的文件进行编译。 **/E**也会从输出文件禁止显示 **/FA**， **/Fa**，并且 **/Fm**选项。 有关详细信息，请参阅[/FA、 /Fa （列表文件）](../../build/reference/fa-fa-listing-file.md)并[/Fm （命名映射文件）](../../build/reference/fm-name-mapfile.md)。

若要禁止显示`#line`指令，使用[/EP （不预处理到 stdout #line 指令)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)选项。

若要将预处理的输出发送到文件而不是`stdout`，使用[/P （预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)选项。

若要禁止显示`#line`指令和发送到文件中，预处理的输出使用 **/P**并 **/EP**在一起。

不能使用预编译标头 **/E**选项。

请注意，当预处理到单独的文件时，未在标记后发出空格。 这可以导致非法的程序或具有意外的副作用。 已成功编译以下程序：

```
#define m(x) x
m(int)main( )
{
   return 0;
}
```

但是，如果使用进行编译：

```
cl -E test.cpp > test2.cpp
```

`int main` 在 test2.cpp 错误地将`intmain`。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 键入中的编译器选项**其他选项**框。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。

## <a name="example"></a>示例

下面的命令行对进行预处理`ADD.C`，保留注释，添加`#line`指令，并在标准输出设备上显示结果：

```
CL /E /C ADD.C
```

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)