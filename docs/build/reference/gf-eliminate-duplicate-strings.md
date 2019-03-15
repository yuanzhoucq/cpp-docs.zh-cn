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
ms.openlocfilehash: 2f2bec446fcec522857b4c05a34311e6c26c9b75
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812312"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF（消除重复的字符串）

使编译器能够在执行过程中在程序映像和内存中创建相同字符串的单个副本。 这是一种优化称为*字符串池*，可以创建较小的程序。

## <a name="syntax"></a>语法

```
/GF
```

## <a name="remarks"></a>备注

如果您使用 **/GF**，操作系统不交换内存的字符串部分，字符串将从图像文件进行读取。

**/GF**池为只读的字符串。 如果你尝试在下修改字符串 **/GF**，应用程序出错时。

字符串池允许用作多个缓冲区的多个指针是多个指向一个缓冲区。 在下面的代码中，`s`和`t`使用相同的字符串初始化。 字符串池使它们指向相同的内存：

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
>  [/ZI](z7-zi-zi-debug-information-format.md)选项，用于编辑并继续，将自动设置 **/GF**选项。

> [!NOTE]
>  **/GF**编译器选项会创建每个唯一字符串的可寻址节。 并且默认情况下的对象文件可以包含最多 65536 可寻址节。 如果您的程序包含多个 65,536 字符串，使用[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)编译器选项来创建更多部分。

**/GF**是在时生效[/o1](o1-o2-minimize-size-maximize-speed.md)或 **/o2**使用。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**代码生成**属性页。

1. 修改**启用字符串池**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
