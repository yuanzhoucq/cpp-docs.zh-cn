---
title: 在 Visual Studio 中连接到你的目标 Linux 系统
description: 如何从 Visual Studio C++ 项目内连接到远程 Linux 计算机或 WSL。
ms.date: 09/04/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 3d91faa7aa83c86e8c2f3544ee61c16f75f8c346
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626769"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>在 Visual Studio 中连接到你的目标 Linux 系统

::: moniker range="vs-2015"

Linux 支持在 Visual Studio 2017 及更高版本中提供。

::: moniker-end

::: moniker range=">=vs-2017"

可以将 Linux 项目配置为以远程计算机或适用于 Linux 的 Windows 子系统 (WSL) 为目标。 对于远程计算机，以及 Visual Studio 2017 上的 WSL，需要设置远程连接。 

## <a name="connect-to-a-remote-linux-computer"></a>连接到远程 Linux 计算机

在为远程 Linux 系统（VM 或物理计算机）生成 C++ Linux 项目时，将 Linux 源代码复制到远程 Linux 计算机，然后基于 Visual Studio 设置进行编译。

若要设置此远程连接，请执行以下操作：

1. 首次生成项目或手动创建新条目的方法：选择“**工具 > 选项**”，然后打开“**跨平台 > 连接管理器**”节点，单击“**添加**”按钮。

   ![连接管理器](media/settings_connectionmanager.png)

   在任一方案中，均将显示“**连接到远程系统**”窗口。

   ![连接到远程系统](media/connect.png)

1. 输入以下信息：

   | 条目 | 说明
   | ----- | ---
   | **主机名**           | 目标设备的名称或 IP 地址
   | **端口**                | 运行 SSH 服务的端口，通常为 22
   | **用户名**           | 要进行身份验证的用户
   | **身份验证类型** | 同时支持密码或私钥
   | **密码**            | 输入的用户名的密码
   | **私钥文件**    | 为 ssh 连接创建的私钥文件
   | **密码**          | 与上面选择的私钥一起使用的密码

   可以使用密码或密钥文件和密码进行身份验证。 对于许多开发方案，密码身份验证已足够。 如果喜欢使用公钥/私钥文件，可以创建一个新的文件或[重用现有文件](https://security.stackexchange.com/questions/10203/reusing-private-public-keys)。 目前仅支持 RSA 和 DSA 密钥。 
   
   可通过以下步骤创建 RSA 私钥文件：

    1. 在 Windows 计算机上，使用 `ssh-keygen -t rsa` 创建 ssh 密钥对。 这将创建一个公钥和一个私钥。 默认情况下，密钥置于 `C:\Users\%USERNAME%\.ssh` 下，名称为 `id_rsa.pub` 和 `id_rsa`。

    1. 从 Windows 中，将公钥复制到 Linux 计算机：`scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`。

    1. 在 Linux 系统上，将密钥添加到授权密钥列表（并确保该文件具有正确的权限）：`cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. 单击“**连接**”按钮，尝试连接到远程计算机。 

   如果连接成功，Visual Studio 将开始配置 IntelliSense，以使用远程标头。 有关详细信息，请参阅[远程系统上标头的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

   如果连接失败，则需要更改的输入框的边框为红色。

   ![连接管理器错误](media/settings_connectionmanagererror.png)

   如果使用密钥文件进行身份验证，请确保目标计算机的 SSH 服务器正在运行且配置正确。

   ::: moniker-end

   ::: moniker range="vs-2019"

   转到“工具”>“选项”>“跨平台”>“日志记录”  以启用日志记录，帮助故障排除连接问题：

   ![远程日志记录](media/remote-logging-vs2019.png)

   日志包括连接、发送到远程计算机的所有命令（其文本、退出代码和执行时间）以及从 Visual Studio 到 shell 的所有输出。 日志记录适用于 Visual Studio 中的任何跨平台 CMake 项目或基于 MSBuild 的 Linux 项目。

   你可以配置输出，以转到一个文件或转到“输出窗口”中的“跨平台日志记录”  窗格。 对于基于 MSBuild 的 Linux 项目，MSBuild 发出到远程计算机的命令不会路由到“输出窗口”  ，因为它们发出到进程外。 相反，它们将记录到前缀为“msbuild_”的文件。
   
## <a name="tcp-port-forwarding"></a>TCP 端口转发

Visual Studio 的 Linux 支持依赖于 TCP 端口转发。 如果在远程系统上禁用了 TCP 端口转发，则 Rsync  和 gdbserver  将会受到影响。 

Rsync 由基于 MSBuild 的 Linux 项目和 CMake 项目用来[将标题从远程系统复制到 Windows，以用于 IntelliSense](configure-a-linux-project.md#remote_intellisense)。 如果无法启用 TCP 端口转发，则可以通过“工具”>“选项”>“跨平台”>“连接管理器”>“远程标头 IntelliSense 管理器”来禁用远程标头的自动下载。 如果你尝试连接的远程系统未启用 TCP 端口转发，则在开始下载 IntelliSense 的远程标头时，会看到以下错误。

![标头错误](media/port-forwarding-headers-error.png)

Visual Studio 的 CMake 支持也使用 Rsync 将源文件复制到远程系统。 如果无法启用 TCP 端口转发，则可以将 sftp 用作远程复制源方法。 sftp 通常会比 rsync 慢，但不依赖于 TCP 端口转发。 你可以在 [CMake 设置编辑器](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects)中，借助 remoteCopySourcesMethod 属性来管理远程复制源方法。 如果在远程系统上禁用了 TCP 端口转发，则在第一次调用 rsync 时，会在 CMake 输出窗口中看到一条错误。

![rsync 错误](media/port-forwarding-copy-error.png)

gdbserver 可用于在嵌入式设备上进行调试。 如果无法启用 TCP 端口转发，则需要对所有远程调试方案使用 gdb。 在远程系统上调试项目时，默认情况下使用 gdb。 

   ::: moniker-end

## <a name="connect-to-wsl"></a>连接到 WSL

::: moniker range="vs-2017"

在 Visual Studio 2017 中，使用如本文前面部分中所述的连接到远程 Linux 计算机的相同步骤连接到 WSL。 使用 localhost  作为主机名  。

::: moniker-end

::: moniker range="vs-2019"

对结合使用 C++ 与[适用于 Linux 的 Windows 子系统 (WSL)](https://docs.microsoft.com/windows/wsl/about)，Visual Studio 2019 版本 16.1 添加了本机支持。  这意味着在本地 WSL 安装上进行生成和调试不再需要添加远程连接或配置 SSH。 可在此处找到有关[如何安装 WSL](https://docs.microsoft.com/windows/wsl/install-win10)的详细信息。

要将 WSL 安装配置为可与 Visual Studio 结合使用，需要安装以下工具：gcc 或 clang、gdb、make、rsync 和 zip。 你可以使用此命令将它们安装在使用 apt 的发行版上，这还将安装 g++ 编译器： 

```bash
sudo apt install g++ gdb make rsync zip
```
有关详细信息，请参阅[下载、安装和设置 Linux 工作负荷](download-install-and-setup-the-linux-development-workload.md)。

若要为 WSL 配置项目，请参阅[配置 Linux 项目](configure-a-linux-project.md)或[配置 Linux CMake 项目](cmake-linux-project.md)，具体取决于你的项目类型。 要按照分步说明使用 WSL 创建简单的控制台应用程序，请参阅关于 [C++ with Visual Studio 2019 and the Windows Subsystem for Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/)（结合使用 C++ 和 Visual Studio 2019 及适用于 Linux 的 Windows 子系统 (WSL)）的介绍性博客文章。

::: moniker-end

## <a name="see-also"></a>另请参阅

[配置 Linux 项目](configure-a-linux-project.md)<br />
[配置 Linux CMake 项目](cmake-linux-project.md)<br />
[部署、运行和调试 Linux 项目](deploy-run-and-debug-your-linux-project.md)<br />
[配置 CMake 调试会话](../build/configure-cmake-debugging-sessions.md)
