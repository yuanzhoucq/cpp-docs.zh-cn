---
title: 在 Visual Studio 中连接到你的目标 Linux 系统
description: 如何从 Visual Studio C++ 项目内连接到远程 Linux 计算机或 WSL。
ms.date: 06/19/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 7fa09c49df3da39084edb6735a7a2ccc724c34d3
ms.sourcegitcommit: 3ae8025df7fd50f5f56a0a2b5396533218bcc7dc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/20/2019
ms.locfileid: "67285262"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>在 Visual Studio 中连接到你的目标 Linux 系统

::: moniker range="vs-2015"

Linux 支持在 Visual Studio 2017 及更高版本中提供。

::: moniker-end

::: moniker range=">=vs-2017"

可以将 Linux 项目配置为以远程计算机或适用于 Linux 的 Windows 子系统 (WSL) 为目标。 对于远程计算机，以及 Visual Studio 2017 上的 WSL，需要设置连接。 

## <a name="connect-to-a-remote-linux-computer"></a>连接到远程 Linux 计算机

在为远程 Linux 系统（VM 或物理计算机）生成 C++ Linux 项目时，将 Linux 代码复制到远程 Linux 计算机，然后基于 Visual Studio 设置进行编译。

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

   ::: moniker-end

## <a name="connect-to-wsl"></a>连接到 WSL

::: moniker range="vs-2017"

在 Visual Studio 2017 中，使用如本文前面部分中所述的连接到远程 Linux 计算机的相同步骤连接到 WSL。 使用 localhost  作为主机名  。

::: moniker-end

::: moniker range="vs-2019"

在 Visual Studio 2019 版本 16.1 中，在以 WSL 为目标时，无需再添加远程连接或配置 SSH。 在 Linux 系统上，只需要 gcc、gdb、make、rsync 和 zip。 Visual Studio 需要 rsync 和 zip 只是为了在从 WSL 实例第一次使用时将标头文件提取到 Windows 文件系统，以用于 IntelliSense。 在 Visual Studio 2019 版本 16.1 中，WSL 支持基于 Windows 版本 1809。 你可以运行更高版本的 Windows，但 Visual Studio 尚未利用新的 WSL 功能。

如果你的发行版支持 apt，可以使用以下命令安装所需的包：

```bash
sudo apt install g++ gdb make rsync zip
```

若要为 WSL 配置项目，请参阅[配置 Linux 项目](configure-a-linux-project.md)或[配置 Linux CMake 项目](cmake-linux-project.md)，具体取决于你的项目类型。

::: moniker-end

## <a name="see-also"></a>另请参阅

[配置 Linux 项目](configure-a-linux-project.md)<br />
[配置 Linux CMake 项目](cmake-linux-project.md)<br />
[部署、运行和调试 Linux 项目](deploy-run-and-debug-your-linux-project.md)<br />




