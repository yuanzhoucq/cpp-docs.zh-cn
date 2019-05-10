---
title: /Fm（命名映射文件）
ms.date: 11/04/2016
f1_keywords:
- /fm
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
ms.openlocfilehash: eebb1bc0c553dba1934aea75e2e63edc0f222fff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292394"
---
# <a name="fm-name-mapfile"></a>/Fm（命名映射文件）

通知链接器生成映射文件包含在相应的.exe 文件或 DLL 中的显示的顺序中的段的列表。

## <a name="syntax"></a>语法

```
/Fmpathname
```

## <a name="remarks"></a>备注

默认情况下，映射文件授予相应的 C 的基名称或C++使用的源文件。扩展名映射。

指定 **/Fm**假定指定具有相同的效果[/MAP （生成映射文件）](map-generate-mapfile.md)链接器选项。

如果指定[/c （编译而无需链接）](c-compile-without-linking.md)以取消链接， **/Fm**不起作用。

映射文件中的全局符号通常有一个或多个前导下划线，因为编译器将变量名称上添加前导下划线。 出现在映射文件中的多个全局符号是由编译器和标准库在内部使用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](output-file-f-options.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[指定路径名](specifying-the-pathname.md)
