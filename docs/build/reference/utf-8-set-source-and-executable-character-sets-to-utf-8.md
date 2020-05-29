---
title: /utf-8 （将源和可执行字符集设置UTF-8为）
ms.date: 04/26/2020
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
no-loc:
- UTF
- UTF-8
- UTF-16
ms.openlocfilehash: c98a30b0ec4b36b8bd87fb0956d9382751975cfd
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168860"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-opno-locutf-8"></a>`/utf-8`（将源和可执行字符集设置UTF-8为）

将源字符集和执行字符集同时指定为UTF-8。

## <a name="syntax"></a>语法

> **`/utf-8`**

## <a name="remarks"></a>备注

可以使用**`/utf-8`** 选项指定使用UTF-8编码的源和执行字符集。 它相当于在命令**`/source-charset:utf-8 /execution-charset:utf-8`** 行上指定。 默认情况下，这些选项中**`/validate-charset`** 的任何一个都启用了选项。 有关支持的代码页标识符和字符集名称的列表，请参阅[代码页标识符](/windows/win32/Intl/code-page-identifiers)。

默认情况下，Visual Studio 会检测字节顺序标记，以确定源文件是否为编码的 Unicode 格式，例如UTF-16或。 UTF-8 如果未找到字节顺序标记，则假定使用当前用户代码页对源文件进行编码，除非已使用**`/utf-8`** 或**`/source-charset`** 选项指定了代码页。 Visual Studio 允许使用多个字符编码中的任意一种来保存 c + + 源代码。 有关源和执行字符集的信息，请参阅语言文档中的[字符集](../../cpp/character-sets.md)。

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>在 Visual Studio 中或以编程方式设置选项

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > " "**c/c + +** > **命令行**" 属性页。

1. 在 "**其他选项**" 中**`/utf-8`** ，添加选项以指定首选编码。

1. 选择“确定”以保存更改****。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/execution-charset （设置执行字符集）](execution-charset-set-execution-character-set.md)<br/>
[/source-charset（设置源字符集）](source-charset-set-source-character-set.md)<br/>
[/validate-charset（验证兼容的字符）](validate-charset-validate-for-compatible-characters.md)
