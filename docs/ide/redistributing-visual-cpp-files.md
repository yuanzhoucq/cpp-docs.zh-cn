---
title: "重新分发 Visual C++ 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "应用程序部署 [C++], 文件重新分发"
  - "部署应用程序 [C++], 文件重新分发"
  - "文件重新分发 [C++]"
  - "重新分发应用程序 [C++]"
  - "重新分发应用程序 [C++], 关于重新分发应用程序"
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
caps.latest.revision: 50
caps.handback.revision: 48
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 重新分发 Visual C++ 文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

部署应用程序时，还必须部署支持该应用程序所需的文件。  如果其中有任何文件由 Microsoft 提供，请检查是否允许你重新发布这些文件。  若要查看 Microsoft 软件许可条款，请参阅 Visual Studio 安装目录或 Visual Studio 安装媒体中的 License.htm。  若要查看某些版本的 Visual Studio 的 Microsoft 软件许可条款中“可分发代码”部分引用的“REDIST 列表”，请参阅 Microsoft 网站上的 [Microsoft Visual Studio 2013 和 Microsoft Visual Studio 2013 SDK 的可分发代码](http://go.microsoft.com/fwlink/p/?LinkId=313603)。  有关可再发行文件的详细信息，请参阅[确定要重新分发的 DLL](../ide/determining-which-dlls-to-redistribute.md) 和[部署示例](../ide/deployment-examples.md)。  
  
 若要部署可再发行 Visual C\+\+ 文件，可以使用包含在 Visual Studio 中的 Visual C\+\+ 可再发行包（VCRedist\_x86.exe、VCRedist\_x64.exe 或 VCRedist\_arm.exe）。  可以在 Program Files \[\(x86\)\]\\Microsoft Visual Studio *版本*\\VC\\redist\\*区域设置*\\ 中的 Visual Studio 安装目录下找到这些文件。  另一个选项是使用可再发行合并模块（.msm 文件），可以在 Program Files \[\(x86\)\]\\Common Files\\Merge Modules\\ 中找到这些模块。  还可以在*应用程序本地文件夹*（这是包含可执行应用程序文件的文件夹）中直接安装可再发行 Visual C\+\+ DLL。  出于维护原因，不建议使用此安装位置。  
  
 Visual C\+\+ Redistributable Package 将安装并注册所有 Visual C\+\+ 库。  如果你使用其中一个包，则必须将其设置为在目标系统上运行，以此作为安装应用程序的先决条件。  我们建议你在部署中使用这些包，因为它们能够启用 Visual C\+\+ 库的自动更新。  有关如何使用这些包的示例，请参阅[演练：使用 Visual C\+\+ 可再发行组件包部署 Visual C\+\+ 应用程序](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
 每个 Visual C\+\+ 可再发行包都会检查计算机上是否存在较新版本。  如果找到较新版本，则不安装包。  从 Visual Studio 2015 开始，可再发行包会显示一个表明安装失败的错误消息。  如果使用 **\/quiet** 标志运行包，则不会显示错误消息。  在任一情况下，Microsoft 安装程序都会记录错误，并且会将错误结果返回给调用方。  从 Visual Studio 2015 包开始，可以检查一个注册表值以确定是否安装了较新版本。  当前安装的版本会作为 REG\_SZ 值存储在 HKEY\_LOCAL\_MACHINE\\SOFTWARE\[\\Wow6432Node\]\\Microsoft\\DevDiv\\vc\\Servicing\\14.0\\RuntimeMinimum 中的“版本”键中。  如果当前安装的版本更新，则无需安装可再发行包。  
  
 如果使用包含 Visual C\+\+ DLL 的合并模块，则必须将该模块包含在用于部署应用程序的 Windows Installer 包（或类似的安装包）中。  有关详细信息，请参阅[使用合并模块重新发布](../ide/redistributing-components-by-using-merge-modules.md)。  有关示例，请参阅[演练：使用安装项目部署 Visual C\+\+ 应用程序](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)，该演练还演示了如何使用 InstallShield Limited Edition 创建安装包。  
  
## 可能的运行时错误  
 如果 Visual C\+\+ 库 DLL 不可访问，并且 Windows 无法为应用程序加载此 DLL，则可能会显示以下消息：**“没有找到 MSVCR\<版本号\>.dll，因此这个应用程序未能启动。重新安装应用程序可能会修复此问题。”**  
  
 若要解决这种错误，请确保你的应用程序正确生成，并且 Visual C\+\+ 库正确部署到目标系统中。  有关详细信息，请参阅[了解 Visual C\+\+ 应用程序的依赖项](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。  
  
## 相关主题  
  
|标题|描述|  
|--------|--------|  
|[使用合并模块重新发布](../ide/redistributing-components-by-using-merge-modules.md)|描述如何使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 可再发行合并模块将 Visual C\+\+ 运行库作为共享 DLL 安装到 %windir%\\system32\\ 文件夹中。|  
|[重新分发 Visual C\+\+ ActiveX 控件](../ide/redistributing-visual-cpp-activex-controls.md)|描述如何重新发布使用 ActiveX 控件的应用程序。|  
|[重新分发数据库支持文件](../ide/redistributing-database-support-files.md)|讨论如何重新发布用于数据访问对象 \(DAO\) 以及 Microsoft 数据访问 SDK 中的数据库技术的支持文件。|  
|[重新分发 MFC 库](../ide/redistributing-the-mfc-library.md)|描述如何重新发布使用 MFC 的应用程序。|  
|[重新分发 ATL 应用程序](../ide/redistributing-an-atl-application.md)|描述如何重新发布使用 ATL 的应用程序。  从 Visual Studio 2012 开始，无需 ATL 的可再发行库。|  
|[部署示例](../ide/deployment-examples.md)|指向演示如何部署 Visual C\+\+ 应用程序的示例的链接。|  
|[部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)|介绍 Visual C\+\+ 部署概念和技术。|