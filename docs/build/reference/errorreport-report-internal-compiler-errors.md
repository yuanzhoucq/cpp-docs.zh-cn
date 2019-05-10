---
title: /errorReport（报告内部编译器错误）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
- /errorreport
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
ms.openlocfilehash: 52909cb42180bf8b778d73fd709be05faf3f5714
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271783"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport（报告内部编译器错误）

允许你直接向 Microsoft 提供内部编译器错误 (ICE) 信息。

## <a name="syntax"></a>语法

```
/errorReport:[ none | prompt | queue | send ]
```

## <a name="arguments"></a>自变量

**none**<br/>
不收集有关内部编译器错误的报告，或不向 Microsoft 发送报告。

**提示**<br/>
当您收到内部编译器错误时，提示您发送报告。 **提示符**时在开发环境中编译应用程序是默认值。

**queue**<br/>
将错误报告排入队列。 当使用管理员权限登录时，将显示一个窗口，以便可以报告自上次登录以来的任何失败 （将不会提示您发送一次每隔三天的故障报告）。 **队列**时在命令提示符下编译应用程序是默认值。

**发送**<br/>
如果报告启用的 Windows 错误报告系统设置自动向 Microsoft 发送内部编译器错误报告。

## <a name="remarks"></a>备注

当编译器无法处理源代码文件时，会导致内部编译器错误 (ICE)。 出现 ICE 时，编译器不会生成可用于修复代码的输出文件或任何有用的诊断。

在早期版本中，当您获得 ICE，感鼓励致电 Microsoft 产品支持服务，以报告问题。 与 **/errorReport**，可以直接向 Microsoft 提供 ICE 信息。 你的错误报告可以帮助改进未来的编译器版本。

用户能否发送报告取决于计算机和用户策略权限。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**高级**属性页。

1. 修改**错误报告**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
