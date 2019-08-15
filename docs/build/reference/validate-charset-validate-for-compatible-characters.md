---
title: /validate-charset（验证兼容的字符）
ms.date: 02/06/2019
f1_keywords:
- /validate-charset
- validate-charset
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
ms.openlocfilehash: 2390aa98b9416eb538f529c8c370c888cccf4734
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498159"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/validate-charset（验证兼容的字符）

验证源文件文本只包含以 UTF-8 表示的字符。

## <a name="syntax"></a>语法

```
/validate-charset[-]
```

## <a name="remarks"></a>备注

您可以使用 **/validate-charset**选项来验证源代码是否只包含可同时用源字符集和执行字符集表示的字符。 当指定 **/source-charset**、 **/execution-charset**或 **/utf-8**编译器选项时, 将自动启用此检查。 可以通过指定 **/validate-charset-** 选项来显式禁用此检查。

默认情况下, Visual Studio 会检测字节顺序标记, 以确定源文件是否为编码的 Unicode 格式, 例如 UTF-16 或 UTF-8。 如果未找到字节顺序标记, 则假定使用当前用户代码页对源文件进行编码, 除非已使用 **/utf-8**或 **/source-charset**选项指定了代码页。 Visual Studio 允许使用多种字符编码C++中的任意一种来保存源代码。 有关源和执行字符集的信息, 请参阅语言文档中的[字符集](../../cpp/character-sets.md)。 有关支持的代码页标识符和字符集名称的列表, 请参阅[代码页标识符](/windows/win32/Intl/code-page-identifiers)。

在源字符集和执行字符集之间进行转换时, Visual Studio 使用 UTF-8 作为内部字符编码。 如果源文件中的字符不能用执行字符集表示, 则 UTF-8 转换将替换问号 "？" 字符。 如果发生这种情况, **/validate-charset**选项会导致编译报告警告。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 展开 "**配置属性**, **C/C++** ,**命令行**" 文件夹。

1. 在 "**其他选项**" 中, 添加 **/validate-charset**选项, 并指定首选编码。

1. 选择“确定”以保存更改。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/execution-charset (设置执行字符集)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset（设置源字符集）](source-charset-set-source-character-set.md)<br/>
[/utf-8（将源和可执行字符集设置为 UTF-8）](utf-8-set-source-and-executable-character-sets-to-utf-8.md)
