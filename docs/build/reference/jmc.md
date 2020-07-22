---
title: /JMC（“仅我的代码”调试）
ms.date: 08/20/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SupportJustMyCode
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: 7b22a754f9f49564cd7f76c7d1989cd562f70874
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373874"
---
# <a name="jmc-just-my-code-debugging"></a>/JMC（“仅我的代码”调试）

为 Visual Studio 调试器中的本机*仅我的代码*调试指定编译器支持。 此选项支持允许 Visual Studio 逐过程执行系统、框架、库和其他非用户调用的用户设置，以及在 "调用堆栈" 窗口中折叠这些调用。 从 Visual Studio 2017 版本15.8 开始，可以使用 **/JMC**编译器选项。

## <a name="syntax"></a>语法

> **/JMC** \[ **-** ]

## <a name="remarks"></a>备注

Visual Studio[仅我的代码](/visualstudio/debugger/just-my-code)设置指定 visual studio 调试器是否逐过程执行系统、框架、库和其他非用户调用。 **/JMC**编译器选项支持在本机 c + + 代码中进行仅我的代码调试。 当启用 **/JMC**时，编译器会 `__CheckForDebuggerJustMyCode` 在函数序言中插入对 helper 函数的调用。 Helper 函数提供支持 Visual Studio 调试器仅我的代码步骤操作的挂钩。 若要启用 Visual Studio 调试器中的仅我的代码，请在菜单栏上选择 "**工具**  >  " "**选项**"，然后在 "**调试**  >  **常规**  >  **启用仅我的代码**" 中设置选项。

**/JMC**选项要求你的代码链接到 C 运行时库（CRT），后者提供了 `__CheckForDebuggerJustMyCode` helper 函数。 如果你的项目未链接到 CRT，你可能会看到链接器错误**LNK2019：无法解析的外部符号 __CheckForDebuggerJustMyCode**。 若要解决此错误，请链接到 CRT，或禁用 **/JMC**选项。

默认情况下， **/JMC**编译器选项是关闭的。 但是，从 Visual Studio 2017 版本15.8 开始，大多数 Visual Studio 项目模板中已启用此选项。 若要显式禁用此选项，请在命令行中使用 **/JMC-** 选项。 在 Visual Studio 中，打开 "项目属性页" 对话框，然后将 "**配置属性**" "c/c + + 常规" 属性页中的 "**支持仅我的代码调试**" 属性更改  >  **C/C++**  >  **General**为 "**否**"。

有关详细信息，请参阅在 visual studio 中[指定是否仅使用仅我的代码调试用户代码](/visualstudio/debugger/just-my-code)中的[c + + 仅我的代码](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code)和 Visual C++ 团队博客文章在[Visual Studio 中公告 c + + 仅我的代码步进](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “C/C++” > “常规”属性页    。

1. 修改**支持仅我的代码调试**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
