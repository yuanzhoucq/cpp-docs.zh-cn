---
title: /validate-charset （验证兼容的字符）
ms.date: 11/04/2016
f1_keywords:
- /validate-charset
- validate-charset
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
ms.openlocfilehash: 243d225f5acde0c6099050539687726ea082c898
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590484"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/validate-charset （验证兼容的字符）

验证源文件文本包含字符仅可表示为 utf-8。

## <a name="syntax"></a>语法

```
/validate-charset[-]
```

## <a name="remarks"></a>备注

可以使用 **/validate-charset**选项来验证源的代码包含仅可在这两个源字符集中表示的字符设置和执行字符集。 指定时，此检查会自动启用 **/source-charset**， **/execution-charset**，或 **/utf-8**编译器选项。 您可以通过指定显式禁用此检查 **/validate-字符集-** 选项。

默认情况下，Visual Studio 会检测以确定源文件是否已编码的 Unicode 格式，例如，utf-16 或 utf-8 字节顺序标记。 如果不找到任何字节顺序标记，则它假定源代码文件的编码使用当前用户的代码页，除非你通过使用指定代码页 **/utf-8**或 **/source-charset**选项。 Visual Studio，可使用任何几个字符编码保存 c + + 源代码。 有关源和执行字符集的信息，请参阅[最小字符集数](../../cpp/character-sets.md)语言文档中。 支持代码页标识符的列表和字符集的名称，请参阅[代码页标识符](/windows/desktop/Intl/code-page-identifiers)。

Visual Studio 使用的源字符集和执行字符集之间的转换过程的内部字符编码为 utf-8。 如果不能在执行字符集中表示源文件中的字符，utf-8 转换将替换为问号？ 字符。 **/Validate-charset**选项将导致编译报告一条警告，如果发生这种情况。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开**配置属性**， **C/c + +**，**命令行**文件夹。

1. 在中**高级选项**，添加 **/validate-charset**选项，并指定你的首选编码。

1. 选择**确定**以保存所做的更改。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[/execution-charset （设置执行字符集）](../../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/source-charset（设置源字符集）](../../build/reference/source-charset-set-source-character-set.md)<br/>
[/utf-8（将源和可执行字符集设置为 UTF-8）](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)