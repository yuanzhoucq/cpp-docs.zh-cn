---
title: 设置符合 FIPS 标准的安全远程 Linux 开发
description: 如何设置 Visual Studio 和 Linux 计算机之间符合 FIPS 的加密连接以用于远程开发。
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "76520461"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>设置符合 FIPS 标准的安全远程 Linux 开发

::: moniker range="<=vs-2017"

Linux 支持在 Visual Studio 2017 及更高版本中提供。 可以在 Visual Studio 2019 版本 16.5 及更高版本中设置符合 FIPS 的安全远程 Linux 开发。

::: moniker-end

::: moniker range="vs-2019"

美国联邦信息处理标准 (FIPS) 出版物 140-2 是美国政府规定的加密模块标准。 此标准的实现由 NIST 进行验证。 Windows [已验证对符合 FIPS 的加密模块的支持](/windows/security/threat-protection/fips-140-validation)。 在 Visual Studio 2019 版本 16.5 及更高版本中，可以对 Linux 系统进行符合 FIPS 的安全加密连接，以用于远程开发。

下面介绍了如何设置 Visual Studio 与远程 Linux 系统之间符合 FIPS 的安全连接。 本指南适用于在 Visual Studio 中生成 CMake 或 MSBuild Linux 项目。 本文是[连接到远程 Linux 计算机](connect-to-your-remote-linux-computer.md)中的连接说明的符合 FIPS 版本。

## <a name="prepare-a-fips-compliant-connection"></a>设置符合 FIPS 的连接的准备工作

必须完成一些准备工作，才能在 Visual Studio 与远程 Linux 系统之间进行符合 FIPS 的安全加密 SSH 连接。 为了符合 FIPS-140-2，Visual Studio 仅支持 RSA 密钥。

本文中的示例结合使用 Ubuntu 18.04 LTS 和 OpenSSH 服务器版本 7.6。 不过，对于任何使用最新版 OpenSSH 的发行版，操作说明应该是相同的。

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>在远程系统上设置 SSH 服务器的具体步骤

1. 在 Linux 系统上，安装并启动 OpenSSH 服务器：

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. 若要让 SSH 服务器在系统启动时自动启动，请使用 systemctl 启用它：

   ```bash
   sudo systemctl enable ssh
   ```

1. 以根用户身份打开 /etc/ssh/sshd_config  。 编辑或添加（若无）以下代码行：

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > ssh-rsa 是 VS 唯一支持的符合 FIPS 的主机密钥算法。 虽然 aes\*-ctr 算法也符合 FIPS，但 Visual Studio 中的实现并未获准。 尽管 ecdh-\* 密钥交换算法符合 FIPS，但并不受 Visual Studio 支持。

   除了这些，还可以使用其他选项。 可以将 SSH 配置为使用其他密码、主机密钥算法等。 不妨考虑使用的其他一些相关安全选项有 `PermitRootLogin`、`PasswordAuthentication` 和 `PermitEmptyPasswords`。 有关详细信息，请参阅 sshd_config 的手册页或 [SSH 服务器配置](https://www.ssh.com/ssh/sshd_config)一文。

1. 保存并关闭 sshd_config 后，重启 SSH 服务器，以应用新配置：

   ```bash
   sudo service ssh restart
   ```

接下来，将在 Windows 计算机上创建 RSA 密钥对。 然后，将公钥复制到远程 Linux 系统，以供 SSH 使用。

### <a name="to-create-and-use-an-rsa-key-file"></a>创建和使用 RSA 密钥文件的具体步骤

1. 在 Windows 计算机上，使用以下命令生成公用/专用 RSA 密钥对：

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   此命令将创建一个公钥和一个私钥。 默认情况下，密钥保存到 %USERPROFILE%\\.ssh\\id_rsa  和 %USERPROFILE%\\.ssh\\id_rsa.pub  。 （在 PowerShell 中，请使用 `$env:USERPROFILE`，而不是 cmd 宏 `%USERPROFILE%`）如果更改密钥名称，请在后续步骤中使用更改后的名称。  为了提高安全性，建议使用密码。

1. 将公钥从 Windows 复制到 Linux 计算机：

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. 在 Linux 系统上，将密钥添加到授权密钥列表中，并确保文件具有正确的权限：

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. 现在，可以测试新密钥在 SSH 中是否有效。 使用它在 Windows 中登录：

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

此时，你已成功设置 SSH、创建和部署加密密钥，并已测试连接。 现在可以设置 Visual Studio 连接了。

## <a name="connect-to-the-remote-system-in-visual-studio"></a>在 Visual Studio 中连接到远程系统

1. 在 Visual Studio 中，依次选择菜单栏上的“工具”>“选项”  ，以打开“选项”  对话框。 然后，依次选择“跨平台”>“连接管理器”  ，以打开“连接管理器”对话框。

   如果你以前没有在 Visual Studio 中设置过连接，Visual Studio 会在你首次生成项目时，为你打开“连接管理器”对话框。

1. 在“连接管理器”对话框中，选择“添加”  按钮，以添加新连接。

   ![连接管理器](media/settings_connectionmanager.png)

   此时，“连接到远程系统”  窗口显示。

   ![连接到远程系统](media/connect.png)

1. 在“连接到远程系统”  对话框中，输入远程计算机的连接详细信息。

   | 条目 | 描述
   | ----- | ---
   | **主机名**           | 目标设备的名称或 IP 地址
   | **端口**                | 运行 SSH 服务的端口，通常为 22
   | **用户名**           | 要进行身份验证的用户
   | **身份验证类型** | 选择用于符合 FIPS 的连接的私钥
   | **私钥文件**    | 为 ssh 连接创建的私钥文件
   | **密码**          | 与上面选择的私钥一起使用的密码

   将“身份验证类型”更改为“私钥”  。 在“私钥文件”  字段中，输入私钥路径。 可以改用“浏览”  按钮转到私钥文件。 然后，在“密码”  字段中输入用于加密私钥文件的密码。

1. 选择“连接”按钮，尝试连接到远程计算机  。

   如果连接成功，Visual Studio 便会将 IntelliSense 配置为使用远程标头。 有关详细信息，请参阅[远程系统上标头的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

   如果连接失败，则需要更改的输入框的边框为红色。

   ![连接管理器错误](media/settings_connectionmanagererror.png)

   若要详细了解如何排查连接问题，请参阅[连接到远程 Linux 计算机](connect-to-your-remote-linux-computer.md)。

## <a name="command-line-utility-for-the-connection-manager"></a>用于连接管理器的命令行实用工具  

**Visual Studio 2019 版本 16.5 或更高版本**：ConnectionManager.exe 是用于在 Visual Studio 之外管理远程开发连接的命令行实用工具。 它对于预配新开发计算机之类的任务非常有用。 你也可以使用它来设置 Visual Studio 进行持续集成。 有关 ConnectionManager 命令的示例和完整参考，请参阅 [ConnectionManager 参考](connectionmanager-reference.md)。  

## <a name="optional-enable-or-disable-fips-mode"></a>可选：启用或禁用 FIPS 模式

可以在 Windows 中全局启用 FIPS 模式。

1. 若要启用 FIPS 模式，请按 Windows+R  以打开“运行”对话框，再运行 gpedit.msc。

1. 依次展开“本地计算机策略”>“计算机配置”>“Windows 设置”>“安全设置”>“本地策略”  ，并选择“安全选项”  。

1. 在“策略”  下，选择“系统加密:  使用符合 FIPS 的算法进行加密、哈希和签名”，然后按 Enter  以打开相应对话框。

1. 在“本地安全设置”  选项卡中，选中“已启用”  或“已禁用”  ，再选择“确定”  ，以保存更改。

> [!WARNING]
> 启用 FIPS 模式可能会导致某些应用程序中断或出现意外行为。 有关详细信息，请参阅博客文章[为什么我们不再推荐“FIPS 模式”](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)。

## <a name="additional-resources"></a>其他资源

[有关 FIPS 140 验证的 Microsoft 文档](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2：加密模块的安全要求](https://csrc.nist.gov/publications/detail/fips/140/2/final)（来自 NIST）

[加密算法验证程序：验证注意事项](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes)（来自 NIST）

Microsoft 博客文章[为什么我们不再推荐“FIPS 模式”](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)

[SSH 服务器配置](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>另请参阅

[配置 Linux 项目](configure-a-linux-project.md)\
[配置 Linux CMake 项目](cmake-linux-project.md)\
[连接到远程 Linux 计算机](connect-to-your-remote-linux-computer.md)\
\[部署、运行和调试 Linux 项目](deploy-run-and-debug-your-linux-project.md)
[配置 CMake 调试会话](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
