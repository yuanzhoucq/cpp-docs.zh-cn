---
title: 在 Visual Studio 中安装 C++ Linux 工作负载
description: 介绍如何在 Visual Studio 中下载、安装和设置用于 C++ 的 Linux 工作负荷。
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: d5c099794f781fa9e6217f3796d24d1a63fd7b53
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042746"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>下载、安装和设置 Linux 工作负载

::: moniker range="vs-2015"

Visual Studio 2017 及更高版本支持 Linux 项目。

::: moniker-end

::: moniker range=">=vs-2017"

可以使用 Windows 中的 Visual Studio IDE 来创建、编辑和调试在 Linux 物理计算机、虚拟机或[适用于 Linux 的 Windows 子系统](/windows/wsl/about)上执行的 C++ 项目。 

可处理使用 CMake 的现有基本代码或任何其他生成系统，无需将其转换为 Visual Studio 项目。 如果基本代码为跨平台代码，则从 Visual Studio 中可同时面向 Windows 和 Linux。 例如，可在 Windows 上使用 Visual Studio 编辑、调试和配置代码，然后快速重定向 Linux 项目以执行进一步测试。 Linux 头文件将自动复制到本地计算机上，Visual Studio 会在该位置使用这些头文件提供完全 IntelliSense 支持（“语句完成”、“转到定义”等）。 
 
对于任何这些方案，都必须拥有“使用 C++ 的 Linux 开发”工作负载  。 

::: moniker-end

::: moniker range="vs-2019"

可在 Visual Studio 2019 中指定用于生成和调试的独立 Linux 目标。 在以 WSL 为目标时，无需再添加远程连接或配置 SSH。

[AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) 支持已集成到适用于 Linux 项目的 Visual Studio。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Visual Studio 安装程序

1. 在 Windows 搜索框中键入“Visual Studio 安装程序”：

   ![Windows 搜索框](media/visual-studio-installer-search.png)

2. 在“应用”结果下寻找安装程序并双击它  。 打开该安装程序后，选择“修改”  ，然后单击“工作负荷”  选项卡。向下滚动到“其他工具集”  ，然后选择  “使用 C++ 的 Linux 开发”工作负荷。

   ![适用于 Linux 开发的 Visual C++ 工作负荷](media/linuxworkload.png)

1. 如果目标是 IoT 或嵌入式平台，请转到“使用 C++ 的 Linux 开发”下右侧的“安装详细信息”窗格，展开“可选组件”，然后选择所需的组件    。 默认情况下，选择适用于 Linux 的 CMake 支持。

1. 单击“修改”  以继续进行安装。

## <a name="options-for-creating-a-linux-environment"></a>用于创建 Linux 环境的选项

如果还没有 Linux 计算机，则可以在 Azure 上创建 Linux 虚拟机。 有关详细信息，请参阅[快速入门：在 Azure 门户中创建 Linux 虚拟机](/azure/virtual-machines/linux/quick-create-portal)。

在 Windows 10 上，可以在适用于 Linux 的 Windows 子系统 (WSL) 上安装你最喜欢的 Linux 发行版以及使该发行版以之为目标。 有关详细信息，请参阅 [Windows 10 的适用于 Linux 的 Windows 子系统安装指南](/windows/wsl/install-win10)。 WSL 是一种方便的控制台环境，但不建议用于图形应用程序。 

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Linux 安装程序：WSL 上的 Ubuntu

以 WSL 为目标时，无需添加远程连接或配置 SSH 即可进行生成和调试。 使用 Visual Studio for Intellisense 支持自动同步 Linux 标头需要 zip 和 rsync   。 如果所需应用程序尚不存在，则可以按如下所述进行安装：

```bash
sudo apt-get install g++ gdb make rsync zip
```
::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>远程 Linux 系统上的 Ubuntu

目标 Linux 系统必须安装 openssh-server、g++、gdb 和 gdbserver，并且必须运行 ssh 守护程序     。  需要压缩才能自动将远程标头与本地计算机同步以获得 Intellisense 支持。 如果这些应用程序尚不存在，则可以按如下所述进行安装：

1. 在 Linux 计算机上的 shell 提示符下，运行：

   ```bash
   sudo apt-get install openssh-server g++ gdb gdbserver zip
   ```

   由于 sudo 命令，可能会提示你输入 root 密码。  如果是这样，输入密码然后继续。 完成后，可安装所需服务和工具。

1. 通过运行以下命令，确保 ssh 服务在 Linux 计算机上运行：

   ```bash
   sudo service ssh start
   ```
   这将启动该服务并在后台运行它，准备接受连接。

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>WSL 上的 Fedora

Fedora 使用 dnf 包安装程序  。 要下载 g++、gdb、rsync 和 zip，请运行     ：

   ```bash
   sudo dnf install gcc-g++ gdb rsync zip
   ```

使用 Visual Studio for Intellisense 支持自动同步 Linux 标头需要 zip 和 rsync   。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>远程 Linux 系统上的 Fedora

运行 Fedora 的目标计算机使用 dnf 包安装程序  。 要下载“openssh-server”、“g++”、“gdb”、“gdbserver”和“zip”并重启 ssh 守护程序，请遵循以下说明      ：

1. 在 Linux 计算机上的 shell 提示符下，运行：

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip
   ```
   由于 sudo 命令，可能会提示你输入 root 密码。  如果是这样，输入密码然后继续。 完成后，可安装所需服务和工具。

1. 通过运行以下命令，确保 ssh 服务在 Linux 计算机上运行：

   ```bash
   sudo systemctl start sshd
   ```

   这将启动该服务并在后台运行它，准备接受连接。

::: moniker-end

::: moniker range="vs-2015"

Visual Studio 2017 及更高版本中提供对 Linux C++ 开发的支持。

::: moniker-end

## <a name="next-steps"></a>后续步骤

现在，可以创建或打开 Linux 项目并将其配置为在目标系统上运行。 有关详细信息，请参见:

- [新建 Linux 项目](create-a-new-linux-project.md)
- [配置 Linux CMake 项目](cmake-linux-project.md)
