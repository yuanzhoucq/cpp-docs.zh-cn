---
title: -J (默认 char 类型是无符号) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
dev_langs:
- C++
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 400985751d9ceebf7cc2c5f632cb33c5ba847bfe
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714280"
---
# <a name="j-default-char-type-is-unsigned"></a>/J（默认 char 类型是无符号的）

将默认 `char` 类型从 `signed char` 更改为 `unsigned char`，并且在将 `char` 类型扩展到 `int` 类型时，将对其进行零扩展。

## <a name="syntax"></a>语法

```
/J
```

## <a name="remarks"></a>备注

如果`char`值显式声明为`signed`，则 **/J**选项不会影响它，且值为符号扩展时它扩展为`int`类型。

**/J**选项定义`_CHAR_UNSIGNED`，这用于`#ifndef`LIMITS.h 文件来定义默认值的范围中`char`类型。

ANSI C 和 c + + 不需要的特定实现`char`类型。 使用最终将被转换为非英语语言的字符数据时，此选项非常有用。

> [!NOTE]
>  如果您将此编译器选项用于 ATL/MFC，则可能产生错误。 尽管您可以通过定义 `_ATL_ALLOW_CHAR_UNSIGNED` 禁用此错误，但此解决方法不受支持可能不会总是有用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。

1. 在项目中**属性页**对话框中，在下的左窗格**配置属性**，展开**C/c + +** ，然后选择**命令行**.

1. 在中**其他选项**窗格中，指定 **/J**编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[使用项目属性](../../ide/working-with-project-properties.md)