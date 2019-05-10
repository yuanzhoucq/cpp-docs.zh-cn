---
title: /utf-8 （设置源和可执行字符集设置为 utf-8）
ms.date: 11/04/2016
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
ms.openlocfilehash: 5ac15c63041e76b8bb0d292868bb982c21866078
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317284"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/utf-8 （设置源和可执行字符集设置为 utf-8）

指定源字符集和执行字符集为 utf-8。

## <a name="syntax"></a>语法

```
/utf-8
```

## <a name="remarks"></a>备注

可以使用 **/utf-8**选项以指定源和执行字符集设置为使用 utf-8 编码。 它相当于同时指定 **/ 无源-charset:utf-8 /execution-charset:utf-8**命令行上。 其中的任何选项还允许 **/validate-charset**默认情况下的选项。 支持代码页标识符的列表和字符集的名称，请参阅[代码页标识符](/windows/desktop/Intl/code-page-identifiers)。

默认情况下，Visual Studio 会检测以确定源文件是否已编码的 Unicode 格式，例如，utf-16 或 utf-8 字节顺序标记。 如果不找到任何字节顺序标记，则它假定源代码文件的编码使用当前用户的代码页，除非你通过使用指定代码页 **/utf-8**或 **/source-charset**选项。 Visual Studio 允许您保存在C++源，方法是使用几个字符编码的任何代码。 有关源和执行字符集的信息，请参阅[最小字符集数](../../cpp/character-sets.md)语言文档中。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 展开**配置属性**， **C /C++**，**命令行**文件夹。

1. 在中**其他选项**，添加 **/utf-8**选项以指定你的首选编码。

1. 选择“确定”以保存更改。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/execution-charset （设置执行字符集）](execution-charset-set-execution-character-set.md)<br/>
[/source-charset（设置源字符集）](source-charset-set-source-character-set.md)<br/>
[/validate-charset（验证兼容的字符）](validate-charset-validate-for-compatible-characters.md)
