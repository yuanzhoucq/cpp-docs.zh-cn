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
ms.openlocfilehash: ed296d339949814dbd796bb5d8e23a406be71c69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269396"
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

ANSI C 和C++不需要的特定实现`char`类型。 使用最终将被转换为非英语语言的字符数据时，此选项非常有用。

> [!NOTE]
>  如果您将此编译器选项用于 ATL/MFC，则可能产生错误。 尽管您可以通过定义 `_ATL_ALLOW_CHAR_UNSIGNED` 禁用此错误，但此解决方法不受支持可能不会总是有用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。

1. 在项目中**属性页**对话框中，在下的左窗格**配置属性**，展开**C /C++**  ，然后选择**命令行**.

1. 在中**其他选项**窗格中，指定 **/J**编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[在 Visual Studio 中设置 C++ 编译器并生成属性](../working-with-project-properties.md)
