---
title: /errorReport（报告内部编译器错误）
description: 引用 Microsoft C/C++编译器/errorReport 命令行选项。
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
ms.openlocfilehash: 9efe96ed2611795e1fef408ad07b49d65261c3b1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075085"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport（报告内部编译器错误）

> [!NOTE]
> **/ErrorReport**选项已弃用。 从 Windows Vista 开始，错误报告由[Windows 错误报告（WER）](/windows/win32/wer/windows-error-reporting)设置控制。

## <a name="syntax"></a>语法

> **/errorReport：** \[**none** \| **prompt** \| **queue** \| **send** ]

## <a name="remarks"></a>备注

编译器无法处理源代码文件时出现内部编译器错误（ICE）结果。 当发生 ICE 时，编译器不会生成输出文件或可以用来修复代码的任何有用的诊断。

**/ErrorReport**参数将被 Windows 错误报告服务设置重写。 如果 Windows 错误报告启用报表，则编译器会自动向 Microsoft 发送内部错误报表。 如果 Windows 错误报告禁用了报表，则不发送任何报表。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 打开 "**配置属性**" > **CC++ /**  > "**高级**" 属性页。

1. 修改**错误报告**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)\
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
