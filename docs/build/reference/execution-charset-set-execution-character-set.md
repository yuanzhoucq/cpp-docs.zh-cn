---
title: /execution-charset (设置执行字符集)
ms.date: 02/06/2019
f1_keywords:
- execution-charset
- /execution-charset
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
ms.openlocfilehash: 44e83524867bc8a914706e1f5b45b61bc4a48087
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492915"
---
# <a name="execution-charset-set-execution-character-set"></a>/execution-charset (设置执行字符集)

允许您为可执行文件指定执行字符集。

## <a name="syntax"></a>语法

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>自变量

*IANA_name*<br/>
IANA 定义的字符集名称。

*CPID*<br/>
代码页标识符。

## <a name="remarks"></a>备注

您可以使用 **/execution-charset**选项来指定执行字符集。 执行字符集是在所有预处理步骤之后向编译阶段输入的程序文本所使用的编码。 此字符集用于编译的代码中的任何字符串或字符文本的内部表示形式。 设置此选项可指定在源文件包含不能在基本执行字符集中表示的字符时要使用的扩展执行字符集。 可以使用 IANA 或 ISO 字符集名称, 也可以使用句点 (.), 后跟3到5位的十进制代码页标识符来指定要使用的字符集。 有关支持的代码页标识符和字符集名称的列表, 请参阅[代码页标识符](/windows/win32/Intl/code-page-identifiers)。

默认情况下, Visual Studio 会检测字节顺序标记, 以确定源文件是否为编码的 Unicode 格式, 例如 UTF-16 或 UTF-8。 如果未找到字节顺序标记, 则假定使用当前用户代码页对源文件进行编码, 除非已使用 **/source-charset**选项或 **/utf-8**选项指定了字符集名称或代码页。 Visual Studio 允许使用多种字符编码C++中的任意一种来保存源代码。 有关源和执行字符集的信息, 请参阅语言文档中的[字符集](../../cpp/character-sets.md)。

如果要将源字符集和执行字符集设置为 UTF-8, 则可以使用 **/utf-8**编译器选项作为快捷方式。 它等效于在命令行上指定 **/source-charset: utf-8/execution-charset: utf-8** 。 默认情况下, 这些选项中的任何一个都启用 **/validate-charset**选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 展开 "**配置属性**, **C/C++** ,**命令行**" 文件夹。

1. 在 "**其他选项**" 中, 添加 **/execution-charset**选项, 并指定首选编码。

1. 选择“确定”以保存更改。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/source-charset（设置源字符集）](source-charset-set-source-character-set.md)<br/>
[/utf-8（将源和可执行字符集设置为 UTF-8）](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset（验证兼容的字符）](validate-charset-validate-for-compatible-characters.md)
