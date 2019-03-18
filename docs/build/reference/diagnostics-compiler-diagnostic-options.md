---
title: /diagnostics （编译器诊断选项）
ms.date: 11/11/2016
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 6b7d043e00204fa191530f03bbed069d71a25fc5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822297"
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/diagnostics （编译器诊断选项）

使用 **/diagnostics**编译器选项来指定所显示的错误和警告的位置信息。

## <a name="syntax"></a>语法

```
/diagnostics:{caret|classic|column}
```

## <a name="remarks"></a>备注

在 Visual Studio 2017 及更高版本支持此选项。

**/Diagnostics**编译器选项控制显示的错误和警告信息。

**/Diagnostics:classic**选项是默认情况下，报告只发现此问题的行数。

**/Diagnostics:column**选项还包括发现此问题的列。 这可以帮助您确定特定的语言构造或导致此问题的字符。

**/Diagnostics:caret**选项包括其中问题找，并将插入符号 (^) 放在其中检测到问题中的代码行的位置下的列。

请注意，在某些情况下，编译器不会检测的问题发生的位置。 例如，缺少分号可能不会检测在遇到其他、 意外符号之前。 报告列和脱字号位于其中编译器检测到出现了问题，它并不总是需要使所做的更正。

**/Diagnostics**选项是从 Visual Studio 2017 开始，提供。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开你的项目**属性页**对话框。

1. 下**配置属性**，展开**C/c + +** 文件夹，然后选择**常规**属性页。

1. 使用中的下拉列表控件**诊断格式**字段来选择诊断显示选项。 选择**确定**或**应用**以保存所做的更改。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
