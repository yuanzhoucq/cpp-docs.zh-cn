---
title: / JMC （仅我的代码调试）
ms.date: 08/20/2018
f1_keywords:
- /JMC
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: a81292b590d96ef93446f9bb59af305c7eda2ef9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516852"
---
# <a name="jmc-just-my-code-debugging"></a>/ JMC （仅我的代码调试）

指定编译器支持的本机*仅我的代码*在 Visual Studio 调试器中进行调试。 此选项支持允许单步执行系统、 框架、 库和其他非用户调用，并折叠这些调用调用堆栈窗口中的 Visual Studio 的用户设置。 **/JMC**编译器选项已从 Visual Studio 2017 版本 15.8 开始提供。

## <a name="syntax"></a>语法

> **/ JMC**\[**-**]

## <a name="remarks"></a>备注

Visual Studio[仅我的代码](/visualstudio/debugger/just-my-code)设置指定是否在 Visual Studio 调试器将逐过程执行系统、 框架、 库和其他非用户调用。 **/JMC**编译器选项启用仅我的代码在你的本机 c + + 代码中进行调试的支持。 当 **/JMC**已启用，编译器将插入到帮助程序函数的调用`__CheckForDebuggerJustMyCode`，函数 prolog 中。 帮助器函数提供挂钩，支持 Visual Studio 调试器仅我的代码的步骤操作。 若要启用仅我的代码在 Visual Studio 调试器中，在菜单栏上，选择**工具** > **选项**，，然后在设置选项**调试** > **常规** > **启用仅我的代码**。

**/JMC**选项要求您的代码链接到 C 运行时库 (CRT)，它提供`__CheckForDebuggerJustMyCode`帮助器函数。 如果在你的项目不会链接到 CRT，可能会看到链接器错误**LNK2019： 无法解析的外部符号 __CheckForDebuggerJustMyCode**。 若要解决此错误，请将链接到 CRT，或禁用 **/JMC**选项。

默认情况下 **/JMC**编译器选项处于关闭状态。 但是，在 Visual Studio 2017 版本 15.8 开始使用此选项将启用大多数 Visual Studio 项目模板。 若要显式禁用此选项，请使用 **/JMC-** 命令行上的选项。 在 Visual Studio 中，打开项目属性页对话框中，并将更改**支持只我的代码进行调试**属性中的**配置属性** > **C/c + +** > **常规**到属性页**否**。

有关详细信息，请参阅[c + + ' 仅我的代码](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code)中[指定是否仅在 Visual Studio 中使用仅我的代码的用户代码进行调试](/visualstudio/debugger/just-my-code)，和 Visual c + + 团队博客文章[宣布推出 c + + 仅我的代码在 Visual Studio 中单步执行](https://blogs.msdn.microsoft.com/vcblog/2018/06/29/announcing-jmc-stepping-in-visual-studio/)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **常规**属性页。

1. 修改**支持只我的代码进行调试**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
