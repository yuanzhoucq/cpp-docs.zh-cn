---
title: -执行-字符集 （设置执行字符集） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution-charset
- /execution-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cd7acf018930c013f477cf4c3a8b3260a8d53ec
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714611"
---
# <a name="execution-charset-set-execution-character-set"></a>/execution-charset （设置执行字符集）

允许您指定可执行文件的执行字符集。

## <a name="syntax"></a>语法

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>自变量

**IANA_name**<br/>
IANA 定义字符集名称。

**CPID**<br/>
代码页标识符。

## <a name="remarks"></a>备注

可以使用 **/execution-charset**选项以指定执行字符集。 执行字符集是用于程序中的所有预处理步骤编译阶段输入的文本的编码。 此字符集用于在已编译的代码中的任何字符串或字符文本的内部表示形式。 设置此选项以指定的源文件包含基本执行字符集中可表示的字符时要使用的扩展的执行字符集。 可以使用任一 IANA 或 ISO 字符集名称，或句点 （.） 后跟 3 至 5 个数字的十进制代码页标识符，以指定要使用的字符集。 支持代码页标识符的列表和字符集的名称，请参阅[代码页标识符](/windows/desktop/Intl/code-page-identifiers)。

默认情况下，Visual Studio 会检测以确定源文件是否已编码的 Unicode 格式，例如，utf-16 或 utf-8 字节顺序标记。 如果不找到任何字节顺序标记，则它假定源代码文件的编码使用当前用户的代码页，除非已指定一个字符设置使用的名称或代码页 **/source-charset**选项或 **/utf-8**选项。 Visual Studio，可使用任何几个字符编码保存 c + + 源代码。 有关源和执行字符集的信息，请参阅[最小字符集数](../../cpp/character-sets.md)语言文档中。

如果你想要将源字符集和执行字符集设置为 utf-8，则可以使用 **/utf-8**编译器选项的快捷方式。 它相当于同时指定 **/ 无源-charset:utf-8 /execution-charset:utf-8**命令行上。 其中的任何选项还允许 **/validate-charset**默认情况下的选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开**配置属性**， **C/c + +**，**命令行**文件夹。

1. 在中**高级选项**，添加 **/execution-charset**选项，并指定你的首选编码。

1. 选择**确定**以保存所做的更改。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[/source-charset （设置源字符集）](../../build/reference/source-charset-set-source-character-set.md)
[/utf-8 （设置源和可执行文件为 utf-8 字符集）](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
[/validate-charset （验证兼容的字符）](../../build/reference/validate-charset-validate-for-compatible-characters.md)