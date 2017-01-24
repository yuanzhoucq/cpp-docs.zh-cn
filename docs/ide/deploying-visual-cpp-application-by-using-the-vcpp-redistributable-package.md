---
title: "演练：使用 Visual C++ 可再发行组件包部署 Visual C++ 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "演练, 使用可再发行组件包部署 Visual C++ 应用程序"
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：使用 Visual C++ 可再发行组件包部署 Visual C++ 应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文分步说明如何使用 Visual C\+\+ 可再发行组件包程序部署 Visual C\+\+ 应用程序。  
  
## 系统必备  
 您必须完成以下组件的组件本演练：  
  
-   安装 Visual Studio 的计算机。  
  
-   另一台没有 Visual C\+\+ 库的计算机。  
  
### 使用 Visual C\+\+ 可再发行组件包程序部署应用程序  
  
1.  按照前三个步骤创建并生成 MFC 应用程序在 [Walkthrough: Deploying a Visual C\+\+ Application By Using a Setup Project](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
2.  创建一个文件，将其命名为 setup.bat，并将下列命令添加到它。  更改 `MyMFCApplication` 到项目的名称。  
  
    ```  
    @echo off  
    vcredist_x86.exe  
    mkdir "C:\Program Files\MyMFCApplication"  
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"  
    ```  
  
3.  创建自解压缩安装文件：  
  
    1.  在一个命令提示符处或在 **运行** 窗口中，运行 iexpress.exe。  
  
    2.  选择 **创建新的自解压缩指令文件** 然后选择 **下一个** 按钮。  
  
    3.  选择 **解压缩文件并运行安装命令** 然后选择 **下一个**。  
  
    4.  在文本框中，输入您的 MFC 应用程序的名称然后选择 **下一个**。  
  
    5.  在 **确认提示** 页上，选择的 **不提示** 然后选择 **下一个**。  
  
    6.  在 **许可协议** 页上，选择的 **不显示许可证** 然后选择 **下一个**。  
  
    7.  在 **打包的文件** 页上，添加以下文件然后选择 **下一个**。  
  
        -   您的 MFC 应用程序 \(.exe 文件\)。  
  
        -   vcredist\_x86.exe。  此文件位于\\ program files \\ Microsoft SDKs \\ windows \\ v7.0A \\ Bootstrapper \\ program 包\\ vcredist\_x86 \\。  
  
        -   您在前面步骤中创建的 setup.bat 文件。  
  
    8.  在 **安装程序将生成** 页上，在 **安装程序** 文本框中，键入以下命令行然后选择 **下一个**。  
  
         **cmd.exe \/c "setup.bat"**  
  
    9. 在 **显示窗口** 页上，选择的 **默认** 然后选择 **下一个**。  
  
    10. 在 **完成的消息** 页上，选择的 **没有消息** 然后选择 **下一个**。  
  
    11. 在 **程序包名称和选项** 页中，输入一个名称为您的自解压缩安装文件，选择 **在包内使用长文件名存储文件** 选项卡，然后选择 **下一个**。  文件名的结尾必须是 Setup.exe \(例如，结尾。  
  
    12. 在 **配置重新启动** 页上，选择的 **不要重新启动** 然后选择 **下一个**。  
  
    13. 在 **保存自提取指令** 页上，选择的 **保存自提取指令 \(SED\) 文件** 然后选择 **下一个**。  
  
    14. 在 **创建包** 页上，选择 **下一个**。  
  
4.  测试在另一台计算机上的自解压缩安装文件，没有 Visual C\+\+ 库：  
  
    1.  在另一台计算机上，请下载设置文件的副本，然后再安装它通过运行并在它提供的步骤之后。  
  
    2.  运行 MFC 应用程序。  
  
         该自解压缩安装文件将安装位于步骤 2 中所指定的文件夹内的 MFC 应用程序。  该应用程序将会成功运行，因为自解压缩安装文件中包含 Visual C\+\+ 可再发行组件包安装程序。  
  
        > [!IMPORTANT]
        >  为确定安装的运行时版本，安装程序检查注册表键值 \\HKLM\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\VC\\Runtimes\\\[platform\]。  如果当前安装的版本比该安装程序尝试安装的版本新，则安装程序在安装的程序页返回成功，无需安装旧版本并使其他入口点项停留在控制面板中。  
  
## 请参阅  
 [部署示例](../ide/deployment-examples.md)