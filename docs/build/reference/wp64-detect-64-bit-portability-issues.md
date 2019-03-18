---
title: /Wp64（检测 64 位可迁移性问题）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
ms.openlocfilehash: 5a3cdaf85fa4dc05ece54fc630cb69fc93650e6b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813937"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64（检测 64 位可迁移性问题）

此编译器选项已过时。 在 Visual Studio 2013 之前的 Visual Studio 版本中，此选项可检测类型的 64 位可移植性问题，这些问题也用 [__w64](../../cpp/w64.md) 关键字标记。

## <a name="syntax"></a>语法

```
/Wp64
```

## <a name="remarks"></a>备注

默认情况下，在 Visual Studio 2013 中之前, 的 Visual Studio 版本 **/wp64**编译器选项生成 32 位 x86 的 MSVC 编译器中处于关闭状态代码，并在 MSVC 编译器中的生成 64 位 x64 代码。

> [!IMPORTANT]
>  [/Wp64](wp64-detect-64-bit-portability-issues.md) 编译器选项和 [__w64](../../cpp/w64.md) 关键字在 Visual Studio 2010 和 Visual Studio 2012 中已弃用，从 Visual Studio 2013 开始不受支持。 如果转换使用此开关的项目，在转换过程中不会迁移该开关。 若要在 Visual Studio 2010 或 Visual Studio 2012 中使用此选项，则必须在项目属性 **“命令行”** 部分中的 **“其他选项”** 下输入编译器开关。 如果在命令行中使用 **/Wp64** 编译器选项，编译器将发出命令行警告 D9002。 而不是使用此选项和关键字来检测 64 位可移植性问题，使用面向 64 位平台的 MSVC 编译器并指定[/w4](compiler-option-warning-level.md)选项。 有关详细信息，请参阅[64 位 x64 目标配置 c + + 项目](../configuring-programs-for-64-bit-visual-cpp.md)。

在 32 位操作系统上测试以下类型的变量，如同在 64 位操作系统上使用的一样：

- int

- long

- 指针

如果通常通过使用生成 64 位 x64 编译器编译你的应用程序代码中，您只需禁用 **/wp64**在 32 位编译中因为 64 位编译器会检测所有问题。 有关如何面向 Windows 64 位操作系统的详细信息，请参阅[64 位 x64 目标配置 c + + 项目](../configuring-programs-for-64-bit-visual-cpp.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页”  对话框。

   有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 修改“附加选项”  框以包括 **/Wp64**。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[配置 64 位 x64 的 c + + 项目目标](../configuring-programs-for-64-bit-visual-cpp.md)
