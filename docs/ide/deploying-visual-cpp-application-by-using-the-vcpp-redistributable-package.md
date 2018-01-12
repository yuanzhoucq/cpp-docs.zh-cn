---
title: "部署应用程序使用的可再发行组件包 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52e3b048f896f0cfd532cb3000617756af2dca92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>演练：使用 Visual C++ 可再发行组件包部署 Visual C++ 应用程序
此步骤说明文章描述如何使用 Visual c + + 可再发行组件包部署 Visual c + + 应用程序。  
  
## <a name="prerequisites"></a>系统必备  
 你必须具有这些组件来完成本演练：  
  
-   安装了 Visual Studio 的计算机。  
  
-   其他计算机未安装 Visual c + + 库。  
  
### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>若要使用 Visual c + + 可再发行组件包来部署应用程序  
  
1.  创建和生成 MFC 应用程序中的前三个步骤[演练： 部署 Visual c + + 应用程序通过使用安装项目](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
2.  创建文件，将其命名为 setup.bat，并将以下命令添加到它。 更改`MyMFCApplication`为你的项目的名称。  
  
    ```cmd
    @echo off  
    vcredist_x86.exe  
    mkdir "C:\Program Files\MyMFCApplication"  
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"  
    ```  
  
3.  创建一个自解压安装文件：  
  
    1.  在命令提示符下或在**运行**窗口中，运行 iexpress.exe。  
  
    2.  选择**创建新自解压缩指令文件**，然后选择**下一步**按钮。  
  
    3.  选择**解压缩文件，然后运行安装命令**，然后选择**下一步**。  
  
    4.  在文本框中，输入你的 MFC 应用程序的名称，然后选择**下一步**。  
  
    5.  上**确认提示**页上，选择**无提示**，然后选择**下一步**。  
  
    6.  上**许可协议**页上，选择**不显示许可证**，然后选择**下一步**。  
  
    7.  上**打包文件**页上，添加以下文件，然后选择**下一步**。  
  
        -   MFC 应用程序 （.exe 文件）。  
  
        -   vcredist_x86.exe。 此文件位于 files\microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\vcredist_x86\\。  
  
        -   你在前面的步骤中创建 setup.bat 文件。  
  
    8.  上**要启动的安装程序**页上，在**安装程序**文本框中，输入以下命令行，然后选择**下一步**。  
  
         **cmd.exe /c"setup.bat"**  
  
    9. 上**显示窗口**页上，选择**默认**，然后选择**下一步**。  
  
    10. 上**完成的消息**页上，选择**任何消息**，然后选择**下一步**。  
  
    11. 上**包名称和选项**页上，输入将自解压缩的安装程序文件，选择的名称**存储使用包内的长文件名的文件**选项，，然后选择**下一步**. 文件名称的结尾必须 Setup.exe—for 示例中，MyMFCApplicationSetup.exe。  
  
    12. 上**配置重新启动**页上，选择**不重新启动**，然后选择**下一步**。  
  
    13. 上**保存自解压缩指令**页上，选择**保存自解压缩指令 (SED) 文件**，然后选择**下一步**。  
  
    14. 上**创建包**页上，选择**下一步**。  
  
4.  测试其他计算机，而不具有 Visual c + + 库上的自解压安装程序文件：  
  
    1.  在其他计算机上，下载一份安装程序文件中，，然后通过运行它，并遵循它提供的步骤中安装它。  
  
    2.  运行 MFC 应用程序。  
  
         自解压的安装程序文件安装的 MFC 应用程序是你在步骤 2 中指定的文件夹中。 由于 Visual c + + 可再发行组件包安装程序包括在自解压缩的安装文件，应用程序将成功运行。  
  
        > [!IMPORTANT]
        >  若要确定安装哪个版本的运行时，安装程序会检查注册表键 \HKLM\SOFTWARE\Microsoft\VisualStudio\11.0\VC\Runtimes\\[平台]。 如果当前安装的版本高于安装正尝试进行安装的版本，安装程序将返回成功，而无需安装较旧版本，并在控制面板的已安装的程序页上留下一个其他项。  
  
## <a name="see-also"></a>请参阅  
 [部署示例](../ide/deployment-examples.md)