---
title: 在 Visual Studio 中部署、运行和调试 C++ Linux 项目
description: 介绍如何从 Visual Studio 中的 C++ Linux 项目内针对远程目标编译、执行和调试代码。
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: df095d5561bea6dac94b9faa139c83c197802bbf
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404406"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>部署、运行和调试 Linux 项目

::: moniker range="vs-2015"

Linux 支持在 Visual Studio 2017 及更高版本中提供。

::: moniker-end

在 Visual Studio 中创建 Linux C++ 项目，并使用 [Linux 连接管理器](connect-to-your-remote-linux-computer.md)连接到该项目后，即可运行和调试该项目。 在远程目标上编译、执行和调试代码。

::: moniker range="vs-2019"

Visual Studio 2019 版本 16.1：可以面向不同 Linux 系统进行调试和生成  。 例如，可以在 x64 系统上进行交叉编译，并在定位 IoT 方案时部署到 ARM 设备。 有关详细信息，请参阅本文后面的[指定用于生成和调试的不同计算机](#separate_build_debug)。

::: moniker-end

与 Linux 项目交互并对其进行调试方法有若干种。

- 使用 Visual Studio 传统功能（例如断点、监视窗口和悬停在变量上）进行调试。 使用这些方法，可以像平常调试其他项目类型那样进行调试。

- 从 Linux 控制台窗口中的目标计算机查看输出。 还可以使用控制台将输入发送到目标计算机。

## <a name="debug-your-linux-project"></a>调试 Linux 项目

1. 在“调试”属性页中选择调试模式  。

   ::: moniker range="vs-2019"

   GDB 用于调试在 Linux 上运行的应用程序。 在远程系统（而非 WSL）上进行调试时，GDB 可以在两种不同的模式下运行，可从项目“调试”属性页中的“调试模式”选项中进行选择   ：

   ![GDB 选项](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB 用于调试在 Linux 上运行的应用程序。 GDB 能以两种不同的模式运行，可从项目“调试”属性页中的“调试模式”选项中进行选择   ：

   ![GDB 选项](media/vs2017-debugger-settings.png)

   ::: moniker-end

   - 在 gdbserver 模式下，GDB 在本地运行，连接到在远程系统上的 gdbserver  。  请注意，这是 Linux 控制台窗口唯一支持的模式。

   - 在 gdb 模式下，Visual Studio 调试程序在远程系统上驱动 GDB  。 如果本地 GDB 版本与目标计算机上安装的版本不兼容，建议选择此选项。 |

   > [!NOTE]
   > 如果不能在 gdbserver 调试模式中命中断点，请尝试 gdb 模式。 必须先将 gdb [安装](download-install-and-setup-the-linux-development-workload.md)在远程目标上。

1. 使用 Visual Studio 中的标准“调试”工作栏，选择远程目标  。

   远程目标可用时，将看见它按名称或 IP 地址列出。

   ![远程目标](media/remote_target.png)

   如果还未连接到远程目标，将会看见使用 [Linux 连接管理器](connect-to-your-remote-linux-computer.md)连接到远程目标的说明。

   ![远程体系结构](media/architecture.png)

1. 在已知将执行的某些代码的左滚动条槽中单击，设置断点。

   设置断点的代码行上出现一个红点。

1. 按 F5（或者“调试”>“开始调试”）开始调试   。

   开始调试时，应用程序先在远程目标上编译，再启动。 任何编译错误都将显示在“错误列表”窗口中  。

   如果没有错误，则应用将启动并且调试程序将在断点处暂停。

   ![命中断点](media/hit_breakpoint.png)

   现在，可通过按命令键（如 F10 或 F11），与处于当前状态的应用程序交互、查看变量以及逐行执行代码   。

1. 如果需要使用 Linux 控制台与应用进行交互，请选择“调试”>“Linux 控制台”  。

   ![Linux 控制台菜单](media/consolemenu.png)

   此控制台将显示来自目标计算机的全部控制台输出并接收输入，然后将其发送到目标计算机。

   ![Linux 控制台窗口](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-based-projects"></a>配置其他调试选项（基于 MSBuild 的项目）

- 可以使用项目“调试”属性页中的“程序参数”项将命令行参数传递给可执行文件   。

   ![程序参数](media/settings_programarguments.png)

- 可使用“**其他调试程序命令**”条目将特定调试程序选项传递到 GDB。  例如，你可能需要忽略 SIGILL（非法指令）信号。  可以使用 handle  命令实现此目的，方法是将以下命令添加到上图所示的“其他调试程序命令”  条目：

   `handle SIGILL nostop noprint`

## <a name="configure-other-debugging-options-cmake-projects"></a>配置其他调试选项（CMake 项目）

可以在 launch.vs.json 文件中为 CMake 项目指定其他命令行参数。 有关详细信息，请参阅[调试 CMake 项目](cmake-linux-project.md#debug_cmake_project)

## <a name="debug-with-attach-to-process"></a>使用“附加到进程”进行调试

Visual Studio 项目的[调试](prop-pages/debugging-linux.md)属性页和 CMake 项目的 Launch.vs.json 设置具有允许附加到正在运行的进程的设置  。 如果需要除了这些设置中提供的控制外的其他控制，则可以将名为 `Microsoft.MIEngine.Options.xml` 的文件置于解决方案或工作区的根路径中。 下面是一个简单的示例：

```xml
<?xml version="1.0" encoding="utf-8"?>
<SupplementalLaunchOptions>
    <AttachOptions>
      <AttachOptionsForConnection AdditionalSOLibSearchPath="/home/user/solibs">
        <ServerOptions MIDebuggerPath="C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\Common7\IDE\VC\Linux\bin\gdb\7.9\x86_64-linux-gnu-gdb.exe"
ExePath="C:\temp\ConsoleApplication17\ConsoleApplication17\bin\x64\Debug\ConsoleApplication17.out"/>
        <SetupCommands>
          <Command IgnoreFailures="true">-enable-pretty-printing</Command>
        </SetupCommands>
      </AttachOptionsForConnection>
    </AttachOptions>
</SupplementalLaunchOptions>
```

AttachOptionsForConnection 具有你可能需要的大多数属性  。 上述示例展示了如何指定搜索其他 .so 库的位置。 子元素 ServerOptions 允许改为使用 gdbserver 附加到远程进程  。 若要执行此操作，需要指定本地 gdb 客户端（Visual Studio 2017 中附带的客户端如上所示）和带符号的二进制文件的本地副本。 SetupCommands 元素允许将命令直接传递给 gdb  。 可以在 GitHub 上找到 [LaunchOptions.xsd 架构](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd)中提供的所有选项。

::: moniker range="vs-2019"

## <a name="specify-different-machines-for-building-and-debugging"></a><a name="separate_build_debug"></a>指定用于生成和调试的不同计算机

在 Visual Studio 2019 版本 16.1 中，可以将远程生成计算机与远程调试计算机分开，以便处理基于 MSBuild 的 Linux 项目和面向远程 Linux 计算机的 CMake 项目。 例如，现在可以在 x64 系统上进行交叉编译，并在定位 IoT 方案时部署到 ARM 设备。

### <a name="msbuild-based-projects"></a>基于 MSBuild 的项目

默认情况下，远程调试计算机与远程生成计算机相同（“配置属性”   > “常规”   > “远程生成计算机”  ）。 若要指定新的远程调试计算机，请在解决方案资源管理器中右键单击该项目，然后转到“配置属性” > “调试” > “远程调试计算机”     。  

![Linux 远程调试计算机](media/linux-remote-debug-machine.png)

“远程调试计算机”的下拉菜单中填充了所有已建立的远程连接  。 若要添加新的远程连接，请导航到“工具” > “选项” > “跨平台” > “连接管理器”，或者在“快速启动”中搜索“连接管理器”      。 另外，还可以在项目的“属性页”（“配置属性” > “常规” > “远程部署目录”    ）中指定新的远程部署目录。

默认情况下，只会将调试过程所需的文件部署到远程调试计算机。 可以使用解决方案资源管理器  配置将部署到远程调试计算机的源文件。 单击源文件时，可以在解决方案资源管理器的正下方看到其文件属性的预览。

![Linux 可部署文件](media/linux-deployable-content.png)

“内容”  属性指定是否将文件部署到远程调试计算机。 可以导航到“属性页” > “配置管理器”并取消选中“部署”以获取所需配置，通过这种方式完全禁用部署    。

在某些情况下，可能需要对项目的部署进行更多控制。 例如，你要部署的某些文件可能超出解决方案的范围，或者你需要为每个文件或目录自定义远程部署目录。 在这些情况下，将以下代码块附加到 .vcxproj 文件，并将“example.cpp”替换为实际文件名：

```xml

<ItemGroup>
   <RemoteDeploy Include="__example.cpp">
<!-- This is the source Linux machine, can be empty if DeploymentType is LocalRemote -->
      <SourceMachine>$(RemoteTarget)</SourceMachine>
      <TargetMachine>$(RemoteDebuggingTarget)</TargetMachine>
      <SourcePath>~/example.cpp</SourcePath>
      <TargetPath>~/example.cpp</TargetPath>
<!-- DeploymentType can be LocalRemote, in which case SourceMachine will be empty and SourcePath is a local file on Windows -->
      <DeploymentType>RemoteRemote</DeploymentType>
<!-- Indicates whether the deployment contains executables -->
      <Executable>true</Executable>
   </RemoteDeploy>
</ItemGroup>
```

### <a name="cmake-projects"></a>CMake 项目

对于面向远程 Linux 计算机的 CMake 项目，可以在 launch.vs.json 中指定新的远程调试计算机。 默认情况下，“remoteMachineName”的值与 CMakeSettings.json 中的“remoteMachineName”属性同步，该属性对应于远程生成计算机。 这些属性不再需要匹配，launch.vs.json 中“remoteMachineName”的值将指示将哪台远程计算机用于部署和调试。

![CMake 远程调试计算机](media/cmake-remote-debug-machine.png)

IntelliSense 将建议使用包含所有已建立的远程连接的列表。 可以导航到“工具” > “选项” > “跨平台” > “连接管理器”，或者在“快速启动”中搜索“连接管理器”，以便添加新的远程连接      。

如果要完全控制部署，可以将以下代码块附加到 launch.vs.json 文件。 请务必将占位符值替换为实际值：

```json

"disableDeploy": false,
"deployDirectory": "~\foo",
"deploy" : [
   {
      "sourceMachine": "127.0.0.1 (username=example1, port=22, authentication=Password)",
      "targetMachine": "192.0.0.1 (username=example2, port=22, authentication=Password)",
      "sourcePath": "~/example.cpp",
      "targetPath": "~/example.cpp",
      "executable": "false"
   }
]

```

::: moniker-end

## <a name="next-steps"></a>后续步骤

- 要在 Linux 上调试 ARM 设备，请参阅此博客文章：[在 Visual Studio 中调试嵌入式 ARM 设备](https://devblogs.microsoft.com/cppblog/debugging-an-embedded-arm-device-in-visual-studio/)。

## <a name="see-also"></a>请参阅

[C++ 调试属性 (Linux C++)](prop-pages/debugging-linux.md)
