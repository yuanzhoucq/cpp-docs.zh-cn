---
title: /source-charset （设置源字符集）
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: 54f8d4d0edaa310384d19a9c9a188f96ec895eac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318207"
---
# <a name="source-charset-set-source-character-set"></a>/source-charset （设置源字符集）

允许您指定可执行文件的源字符集。

## <a name="syntax"></a>语法

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>自变量

**IANA_name**<br/>
IANA 定义字符集名称。

**CPID**<br/>
以十进制数的代码页标识符。

## <a name="remarks"></a>备注

可以使用 **/source-charset**选项可以指定扩展的源字符设置使用的源文件包括在基本源字符集中未表示的字符时。 源字符集是用于为用作在编译前的预处理阶段输入的内部表示形式解释程序的源文本的编码。 然后，内部表示形式将转换为执行字符集在可执行文件中存储的字符串和字符值。 可以使用任一 IANA 或 ISO 字符集名称，或句点 （.） 后跟 3 至 5 个数字的十进制代码页标识符，以指定要使用的字符集。 支持代码页标识符的列表和字符集的名称，请参阅[代码页标识符](/windows/desktop/Intl/code-page-identifiers)。

默认情况下，Visual Studio 会检测以确定源文件是否已编码的 Unicode 格式，例如，utf-16 或 utf-8 字节顺序标记。 如果不找到任何字节顺序标记，则它假定源代码文件的编码使用当前用户的代码页，除非您指定一个字符设置使用的名称或代码页 **/source-charset**选项。 Visual Studio 允许您保存在C++源，方法是使用几个字符编码的任何代码。 有关源和执行字符集的详细信息，请参阅[最小字符集数](../../cpp/character-sets.md)语言文档中。

你提供的源字符集必须映射到相同的代码点在字符集中的 7 位 ASCII 字符或多个编译错误，可能要遵循。 在源字符集也是可映射到扩展设置 utf-8 编码的 Unicode 字符。 不在 utf-8 中编码的字符由特定于实现的替代表示。 Microsoft 编译器使用的这些字符的问号。

如果你想要将源字符集和执行字符集设置为 utf-8，则可以使用 **/utf-8**编译器选项的快捷方式。 它相当于同时指定 **/ 无源-charset:utf-8 /execution-charset:utf-8**命令行上。 其中的任何选项还允许 **/validate-charset**默认情况下的选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 展开**配置属性**， **C /C++**，**命令行**文件夹。

1. 在中**其他选项**，添加 **/source-charset**选项，并指定你的首选编码。

1. 选择“确定”以保存更改。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/execution-charset （设置执行字符集）](execution-charset-set-execution-character-set.md)<br/>
[/utf-8（将源和可执行字符集设置为 UTF-8）](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset（验证兼容的字符）](validate-charset-validate-for-compatible-characters.md)
