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
ms.openlocfilehash: 49a3d20aee54b06bae2670be139d748fd2aaca6d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469845"
---
# <a name="fm-name-mapfile"></a>/Fm（命名映射文件）

通知链接器生成映射文件包含在相应的.exe 文件或 DLL 中的显示的顺序中的段的列表。

## <a name="syntax"></a>语法

```
/Fmpathname
```

## <a name="remarks"></a>备注

默认情况下，映射文件授予与相应的 C 或 c + + 源代码文件的基名称。扩展名映射。

指定 **/Fm**假定指定具有相同的效果[/MAP （生成映射文件）](../../build/reference/map-generate-mapfile.md)链接器选项。

如果指定[/c （编译而无需链接）](../../build/reference/c-compile-without-linking.md)以取消链接， **/Fm**不起作用。

映射文件中的全局符号通常有一个或多个前导下划线，因为编译器将变量名称上添加前导下划线。 出现在映射文件中的多个全局符号是由编译器和标准库在内部使用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](../../build/reference/output-file-f-options.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[指定路径名](../../build/reference/specifying-the-pathname.md)