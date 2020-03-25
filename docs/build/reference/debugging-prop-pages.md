---
title: C++调试属性页
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 78115a6b-3799-4515-814e-8566b5bdc55d
f1_keywords:
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCLocalDebugPageObject.AmpDefaultAccelerator
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.Environment
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.AmpDefaultAccelerator
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
ms.openlocfilehash: c2190c4406e165cfec1915234b688c598f228777
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169703"
---
# <a name="c-debugging-property-pages"></a>C++调试属性页

这些属性页在 "**项目** > **属性**" 下找到， > **配置属性** > **调试**。 在下拉控件中选择 "调试器类型"。 有关调试C++代码的详细信息，请参阅[教程：学习使用C++ Visual Studio 调试代码](/visualstudio/debugger/getting-started-with-the-debugger-cpp)和[调试本机代码](/visualstudio/debugger/debugging-native-code)。

## <a name="local-windows-debugger-property-page"></a>"本地 Windows 调试器" 属性页

### <a name="command"></a>Command

要执行的调试命令。

### <a name="command-arguments"></a>命令参数

要传递给应用程序的命令行参数。

### <a name="working-directory"></a>工作目录

应用程序的工作目录。 默认情况下，包含项目文件的目录。

### <a name="attach"></a>附加

指定调试器是否应尝试在启动调试时附加到现有进程。

### <a name="debugger-type"></a>调试器类型

指定要使用的调试器类型。 如果设置为 "自动"，则将根据 exe 文件的内容选择调试器类型。

**选项**

- **仅限本机**-仅限本机
- **仅限托管**
- **混合**混合
- **自动**自动
- **脚本**-脚本
- **仅限 GPUC++ （amp）** -仅限C++ gpu （amp）

### <a name="environment"></a>环境

指定要调试的程序的环境，或要与现有环境合并的变量。

### <a name="debugging-accelerator-type"></a>调试加速器类型

用于调试 GPU 代码的调试加速器类型。 （当 GPU 调试器处于活动状态时可用。）

### <a name="gpu-default-breakpoint-behavior"></a>GPU 默认断点行为

设置 GPU 调试器中断的频率。

**选项**

- **每**个弯曲一次中断一次
- 为每个线程**中断（例如 cpu 行为）** -每个线程中断（如 cpu 行为）

### <a name="merge-environment"></a>合并环境

将指定的环境变量与现有环境合并。

### <a name="sql-debugging"></a>SQL 调试

附加 SQL 调试器。

### <a name="amp-default-accelerator"></a>Amp 默认快捷键

覆盖C++ AMP 的默认快捷键选择。 调试托管代码时，属性不适用。

## <a name="remote-windows-debugger-property-page"></a>"远程 Windows 调试器" 属性页

有关远程调试的详细信息，请参阅[在 Visual Studio C++中远程调试视觉对象](/visualstudio/debugger/remote-debugging-cpp)。

### <a name="remote-command"></a>远程命令

要执行的调试命令。

### <a name="remote-command-arguments"></a>远程命令参数

要传递给应用程序的命令行参数。

### <a name="working-directory"></a>工作目录

应用程序的工作目录。 默认情况下，包含项目文件的目录。

### <a name="remote-server-name"></a>“远程服务器名称”

指定远程服务器名称。

### <a name="connection"></a>连接

指定连接类型。

**选项**

- **带 windows 身份验证的远程**-远程和[windows 身份验证](/windows-server/security/windows-authentication/windows-authentication-overview)。
- **不带身份验证的远程远程**身份验证（无身份验证）。

### <a name="debugger-type"></a>调试器类型

指定要使用的调试器类型。 如果设置为 "自动"，则将根据 exe 文件的内容选择调试器类型。

**选项**

- **仅限本机**-仅限本机
- **仅限托管**
- **混合**混合
- **自动**自动
- **脚本**-脚本
- **仅限 GPUC++ （amp）** -仅限C++ gpu （amp）

### <a name="environment"></a>环境

指定要调试的程序的环境，或要与现有环境合并的变量。

### <a name="debugging-accelerator-type"></a>调试加速器类型

用于调试 GPU 代码的调试加速器类型。 （当 GPU 调试器处于活动状态时可用。）

### <a name="gpu-default-breakpoint-behavior"></a>GPU 默认断点行为

设置 GPU 调试器中断的频率。

**选项**

- **每**个弯曲一次中断一次
- 为每个线程**中断（例如 cpu 行为）** -每个线程中断（如 cpu 行为）

### <a name="attach"></a>附加

指定调试器是否应尝试在启动调试时附加到现有进程。

### <a name="sql-debugging"></a>SQL 调试

附加 SQL 调试器。

### <a name="deployment-directory"></a>部署目录

当在远程计算机上进行调试时，如果希望将项目输出的内容（PDB 文件除外）复制到远程计算机，请在此指定路径。

### <a name="additional-files-to-deploy"></a>其他要部署的文件

在远程计算机上进行调试时，此处指定的文件和目录（项目输出除外）将被复制到部署目录（如果已指定）。

### <a name="deploy-visual-c-debug-runtime-libraries"></a>部署 Visual C++ 调试运行时库

指定是否为活动平台（Win32、x64 或 ARM）部署调试运行库。

### <a name="amp-default-accelerator"></a>Amp 默认快捷键

覆盖C++ AMP 的默认快捷键选择。 调试托管代码时，属性不适用。

## <a name="web-browser-debugger-property-page"></a>Web 浏览器调试器属性页

### <a name="http-url"></a>HTTP URL

指定项目的 URL。

### <a name="debugger-type"></a>调试器类型

指定要使用的调试器类型。 如果设置为 "自动"，则将根据 exe 文件的内容选择调试器类型。

**选项**

- **仅限本机**-仅限本机
- **仅限托管**
- **混合**混合
- **自动**自动
- **脚本**-脚本

## <a name="web-service-debugger-property-page"></a>"Web 服务调试器" 属性页

### <a name="http-url"></a>HTTP URL

指定项目的 URL。

### <a name="debugger-type"></a>调试器类型

指定要使用的调试器类型。 如果设置为 "自动"，则将根据 exe 文件的内容选择调试器类型。

**选项**

- **仅限本机**-仅限本机
- **仅限托管**
- **混合**混合
- **自动**自动
- **脚本**-脚本

### <a name="sql-debugging"></a>SQL 调试

附加 SQL 调试器。
