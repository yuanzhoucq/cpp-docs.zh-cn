---
title: 使用可再发行组件包 (C++) 部署应用
ms.date: 09/17/2018
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
ms.openlocfilehash: ccf6b74096894c2e48258e6e0a60b807c7c6c5b4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786231"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>演练：使用 Visual C++ 可再发行软件包部署 Visual C++ 应用程序

本文分步说明了如何使用 Visual C++ 可再发行组件包部署 Visual C++ 应用程序的方法。

## <a name="prerequisites"></a>系统必备

要完成本演练，必须具有以下组件：

- 一台已安装 Visual Studio 的计算机。

- 另一台没有 Visual C++ 库的计算机。

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>使用 Visual C++ 可再发行组件包部署应用程序

1.  请按照[演练：使用安装项目部署 Visual C++ 应用程序](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)中的步骤创建和生成 MFC 应用程序。

1. 创建文件，将其命名为 setup.bat，并向其添加以下命令。 将 `MyMFCApplication` 更改为项目名称。

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

1. 创建自解压安装程序文件：

   1. 在命令提示符处或“运行”窗口中，运行 iexpress.exe。

   1. 选择“新建自解压指令文件”，然后选择“下一步”按钮。

   1. 选择“解压文件并运行安装命令”然后选择“下一步”。

   1. 在文本框中，输入 MFC 应用程序的名称，然后选择“下一步”。

   1. 在“确认提示”页上，选择“无提示”，然后选择“下一步”。

   1. 在“许可协议”页上，选择“不显示许可”，然后选择“下一步”。

   1. 在“包文件”页上，添加以下文件，然后选择“下一步”。

      - MFC 应用程序（.exe 文件）。

      - vcredist_x86.exe。 此文件位于 \Program Files (x86)\Microsoft Visual Studio \<version>\SDK\Bootstrapper\Packages\. 中 也可以从 [Microsoft](https://www.microsoft.com/download/confirmation.aspx?id=5555) 下载此文件。

      - 在之前的步骤中创建的 setup.bat 文件。

   1. 在“安装要启动的程序”页上，在“安装程序”文本框中输入以下命令行，然后选择“下一步”。

      **cmd.exe /c “setup.bat”**

   1. 在“显示窗口”页上，选择“默认”，然后选择“下一步”。

   1. 在“完成消息”页上，选择“无消息”，然后选择“下一步”。

   1. 在“包名和选项”页上，输入自解压安装程序文件的名称，选择“使用包内的长文件名称存储文件”选项，然后选择“下一步”。 文件名的末尾必须是 Setup.exe，例如，*MyMFCApplicationSetup.exe*。

   1. 在“配置重启”页上，选择“不重启”，然后选择“下一步”。

   1. 在“保存自解压指令”页上，选择“保存自解压指令(SED)文件”，然后选择“下一步”。

   1. 在“创建包”页上，选择“下一步”。 选择“完成”。

1. 在另一台没有 Visual C++ 库的计算机上测试自解压安装程序文件：

   1. 在该计算机上，下载安装程序文件的副本，然后通过运行它并按照其提供的步骤进行安装。 根据所选选项，安装可能需要“以管理员身份运行”命令。

   1. 运行 MFC 应用程序。

      自解压安装程序文件可安装在步骤 2 中指定的文件夹中的 MFC 应用程序。 由于 Visual C++ 可再发行组件包安装程序包含在自解压安装程序文件中，因此应用程序成功运行。

      > [!IMPORTANT]
      > 为了确定安装的运行时版本，安装程序会检查注册表项 \HKLM\SOFTWARE\Microsoft\VisualStudio\\\<version>\VC\Runtimes\\<platform>。 如果当前安装的版本比安装程序尝试安装的版本高，则安装程序成功返回而不安装较旧版本，并在控制面板中的已安装程序页上留下其他条目。

## <a name="see-also"></a>请参阅

[部署示例](deployment-examples.md)<br/>
