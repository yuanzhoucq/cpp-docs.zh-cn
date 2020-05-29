---
title: /GF（消除重复的字符串）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
ms.openlocfilehash: e0d23004c7b710f51065db52410fbb15b7cca040
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320493"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF（消除重复的字符串）

使编译器能够在执行期间在程序映像和内存中创建相同字符串的单个副本。 这是一种称为*字符串池的*优化，可以创建较小的程序。

## <a name="syntax"></a>语法

```
/GF
```

## <a name="remarks"></a>备注

如果使用 **/GF**，操作系统不会交换内存的字符串部分，并且可以从映像文件读取字符串。

**/GF**将字符串池为只读字符串。 如果尝试修改 **/GF**下的字符串，则会发生应用程序错误。

字符串池允许用作多个缓冲区的多个指针作为指向单个缓冲区的多个指针。 在以下代码中，`s`使用相同的`t`字符串进行初始化。 字符串池导致它们指向相同的内存：

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
> 用于编辑和继续的[/ZI](z7-zi-zi-debug-information-format.md)选项会自动设置 **/GF**选项。

> [!NOTE]
> **/GF**编译器选项为每个唯一字符串创建一个可寻址部分。 默认情况下，对象文件最多可以包含 65，536 个可寻址部分。 如果程序包含超过 65，536 个字符串，请使用[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)编译器选项创建更多节。

**/GF**在使用[/O1](o1-o2-minimize-size-maximize-speed.md)或[/O2](o1-o2-minimize-size-maximize-speed.md)时生效。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击 **"代码生成"** 属性页。

1. 修改**启用字符串池**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
