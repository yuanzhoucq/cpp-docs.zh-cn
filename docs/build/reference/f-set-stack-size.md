---
title: /F（设置堆栈大小）
ms.date: 11/04/2016
f1_keywords:
- /f
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
ms.openlocfilehash: 31d694c176afd3c79cde172248bfcd93d1346b54
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414442"
---
# <a name="f-set-stack-size"></a>/F（设置堆栈大小）

以字节为单位设置程序堆栈大小。

## <a name="syntax"></a>语法

> **/F** *number*

## <a name="arguments"></a>自变量

*number*<br/>
堆栈大小 （字节）。

## <a name="remarks"></a>备注

如果不使用此选项的堆栈大小默认为 1 MB。 *数*参数可以是以十进制或 C 语言表示法。 参数的范围可以介于 1 到链接器接受的最大堆栈大小。 链接器指定到最接近的 4 个字节的值向上舍入。 之间的间距 **/F**并*数*是可选的。

您可能需要增加堆栈大小，如果您的程序获取堆栈溢出消息。

此外可以设置堆栈大小：

- 使用 **/stack**链接器选项。 有关详细信息，请参阅[/stack](../../build/reference/stack.md)。

- 使用 EDITBIN 的.exe 文件。 有关详细信息，请参阅[EDITBIN 参考](../../build/reference/editbin-reference.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
