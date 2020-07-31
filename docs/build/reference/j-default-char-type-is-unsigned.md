---
title: /J（默认 char 类型是无符号的）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
ms.openlocfilehash: d95fed3d9af81d89ac03a52a1e6433786118430e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223832"
---
# <a name="j-default-char-type-is-unsigned"></a>/J（默认 char 类型是无符号的）

将的默认 **`char`** 类型更改 **`signed char`** 为 **`unsigned char`** ，并且在 **`char`** 将类型扩大到类型时，将类型设置为零扩展 **`int`** 。

## <a name="syntax"></a>语法

```
/J
```

## <a name="remarks"></a>备注

如果将 **`char`** 值显式声明为 **`signed`** ，则 **/j**选项不会影响它，并且在将值扩展到类型时，该值将进行符号扩展 **`int`** 。

**/J**选项定义 `_CHAR_UNSIGNED` ，它 `#ifndef` 在限制 .h 文件中用于定义默认类型的范围 **`char`** 。

ANSI C 和 c + + 不需要类型的特定实现 **`char`** 。 如果使用的字符数据最终将翻译为非英语语言，则此选项很有用。

> [!NOTE]
> 如果您将此编译器选项用于 ATL/MFC，则可能产生错误。 尽管您可以通过定义 `_ATL_ALLOW_CHAR_UNSIGNED` 禁用此错误，但此解决方法不受支持可能不会总是有用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。

1. 在 "项目**属性页**" 对话框的 "**配置属性**" 下的左窗格中，展开 " **C/c + +** "，然后选择 "**命令行**"。

1. 在 "**其他选项**" 窗格中，指定 **/j**编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[在 Visual Studio 中设置 C++ 编译器并生成属性](../working-with-project-properties.md)
