---
title: 在 Visual Studio 中部署、运行和调试 C++ Linux 项目 | Microsoft Docs
description: 介绍如何从 Visual Studio 中的 C++ Linux 项目内针对远程目标编译、执行和调试代码。
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 57f8aea7d3ff3ddfd28beff6647dc16885d972e3
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207674"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>部署、运行和调试 Linux 项目

在 Visual Studio 中创建 Linux C++ 项目，并使用 [Linux 连接管理器](../linux/connect-to-your-remote-linux-computer.md)连接到该项目，即可运行和调试该项目。 在远程目标上编译、执行和调试代码。

与 Linux 项目交互并对其进行调试方法有若干种。

* 使用 Visual Studio 传统功能（例如断点、监视窗口和悬停在变量上）进行调试。 使用这些方法，可以像平常调试其他项目类型那样进行调试。
* 从特殊 Linux 控制台窗口中的目标计算机查看输出。 还可以使用控制台将输入发送到目标计算机。

## <a name="debug-your-linux-project"></a>调试 Linux 项目

1. 在“调试”属性页中选择调试模式。

    GDB 用于调试在 Linux 上运行的应用程序。  但是，能以两种不同的模式运行，可从项目“**调试**”属性页中的“**调试模式**”选项中进行选择：

    ![GDB 选项](media/settings_debugger.png)

    - 在“gdbserver”模式中，GDB 在本地运行，连接到在远程系统上运行的 gdbserver。  请注意，这是 Linux 控制台窗口唯一支持的模式。

    - 在“gdb”模式中，Visual Studio 调试器驱动远程系统上的 GDB，如果 GDB 的本地版本与目标计算机上安装的版本不兼容，则远程系统上的 GDB 更易兼容。 |

    > [!NOTE] 
    > 如果不能在 gdbserver 调试模式中命中断点，请尝试 gdb 模式。 必须先将 gdb [安装](../linux/download-install-and-setup-the-linux-development-workload.md)在远程目标上。

2. 使用 Visual Studio 中的标准“调试”工作栏，选择远程目标。

    远程目标可用时，将看见它按名称或 IP 地址列出。

    ![远程目标](media/remote_target.png)

    如果还未连接到远程目标，将会看见使用 [Linux 连接管理器](../linux/connect-to-your-remote-linux-computer.md)连接到远程目标的说明。

    ![远程体系结构](media/architecture.png)

3. 在已知将执行的某些代码的左滚动条槽中单击，设置断点。

    设置断点的代码行上出现一个红点。

4. 按 F5（或者“调试”>“开始调试”）开始调试。

    开始调试时，应用程序先在远程目标上编译，再启动。 任何编译错误都将显示在“错误列表”窗口中。

    如果没有错误，则应用将启动并且调试程序将在断点处暂停。

    ![命中断点](media/hit_breakpoint.png)  

    现在，可以通过按命令键（如 F10 或 F11），与处于当前状态的应用程序交互、查看变量以及逐行执行代码。

4. 如果需要使用 Linux 控制台与应用进行交互，请选择“调试”>“Linux 控制台”。

  ![Linux 控制台菜单](media/consolemenu.png)

  此控制台将显示来自目标计算机的全部控制台输出并接收输入，然后将其发送到目标计算机。

  ![Linux 控制台窗口](media/consolewindow.png)

## <a name="configure-other-debugging-options"></a>配置其他调试选项

* 可以使用项目“**调试**”属性页中的“**程序参数**”项将命令行参数传递给可执行文件。
  
  ![程序参数](media/settings_programarguments.png)

* 可使用“**其他调试程序命令**”条目将特定调试程序选项传递到 GDB。  例如，你可能需要忽略 SIGILL（非法指令）信号。  那么，可以使用“**句柄**”命令来实现此目的，方法是：  将以下命令添加到如上图中所示的“**其他调试程序命令**”条目：

  ```handle SIGILL nostop noprint```

## <a name="next-steps"></a>后续步骤

* 若要在 Linux 上调试 ARM 设备，请参阅此博客文章：[Debugging an embedded ARM device in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/)（在 Visual Studio 中调试嵌入的 ARM 设备）。

* 若要使用 **Attach to Process** 命令进行调试，请参阅以下博客文章：[Linux C++ Workload improvements to the Project System, Linux Console Window, rsync and Attach to Process](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/)（Linux C++ 工作负载对 Project System、Linux Console Window、rsync 和 Attach to Process 的改进）。

## <a name="see-also"></a>请参阅
[C++ 调试属性 (Linux C++)](../linux/prop-pages/debugging-linux.md)。
