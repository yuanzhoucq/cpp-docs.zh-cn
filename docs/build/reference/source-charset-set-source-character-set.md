---
title: /source-charset (设置源字符集)
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: cd3e4eb3fd305ba6bdd298d18b1edb80f2b98343
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498258"
---
# <a name="source-charset-set-source-character-set"></a>/source-charset (设置源字符集)

允许您指定可执行文件的源字符集。

## <a name="syntax"></a>语法

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>自变量

**IANA_name**<br/>
IANA 定义的字符集名称。

**CPID**<br/>
十进制数形式的代码页标识符。

## <a name="remarks"></a>备注

您可以使用 **/source-charset**选项指定要在源文件包含基本源字符集中未表示的字符时使用的扩展源字符集。 源字符集是用于将程序的源文本解释为在编译之前用于预处理阶段输入的内部表示形式的编码。 然后, 将内部表示形式转换为执行字符集, 以将字符串和字符值存储在可执行文件中。 可以使用 IANA 或 ISO 字符集名称, 也可以使用句点 (.), 后跟3到5位的十进制代码页标识符来指定要使用的字符集。 有关支持的代码页标识符和字符集名称的列表, 请参阅[代码页标识符](/windows/win32/Intl/code-page-identifiers)。

默认情况下, Visual Studio 会检测字节顺序标记, 以确定源文件是否为编码的 Unicode 格式, 例如 UTF-16 或 UTF-8。 如果未找到字节顺序标记, 则假定使用 "当前用户" 代码页对源文件进行编码, 除非使用 **/source-charset**选项指定了字符集名称或代码页。 Visual Studio 允许使用多种字符编码C++中的任意一种来保存源代码。 有关源和执行字符集的详细信息, 请参阅语言文档中的[字符集](../../cpp/character-sets.md)。

您提供的源字符集必须将7位 ASCII 字符映射到字符集中的相同码位, 否则可能会出现许多编译错误。 源字符集还必须可映射到扩展 Unicode 字符集, encodable 通过 UTF-8。 UTF-8 中不 encodable 的字符由特定于实现的替换表示。 Microsoft 编译器对这些字符使用一个问号。

如果要将源字符集和执行字符集设置为 UTF-8, 则可以使用 **/utf-8**编译器选项作为快捷方式。 它等效于在命令行上指定 **/source-charset: utf-8/execution-charset: utf-8** 。 默认情况下, 这些选项中的任何一个都启用 **/validate-charset**选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 展开 "**配置属性**, **C/C++** ,**命令行**" 文件夹。

1. 在 "**其他选项**" 中, 添加 **/source-charset**选项, 并指定首选编码。

1. 选择“确定”以保存更改。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/execution-charset (设置执行字符集)](execution-charset-set-execution-character-set.md)<br/>
[/utf-8（将源和可执行字符集设置为 UTF-8）](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset（验证兼容的字符）](validate-charset-validate-for-compatible-characters.md)
