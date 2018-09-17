---
title: -诊断 （编译器诊断选项） |Microsoft Docs
ms.custom: ''
ms.date: 11/11/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
dev_langs:
- C++
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97b5e3ef2e5c14ae93d4fcc3b016f4dbc955edbd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709158"
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

2. 下**配置属性**，展开**C/c + +** 文件夹，然后选择**常规**属性页。

3. 使用中的下拉列表控件**诊断格式**字段来选择诊断显示选项。 选择**确定**或**应用**以保存所做的更改。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)