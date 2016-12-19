---
title: "确定要重新分发的 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "应用程序部署 [C++], DLL 重新分发"
  - "依赖项 [C++], 应用程序部署与"
  - "部署应用程序 [C++], DLL 重新分发"
  - "DLL [C++], 重新分发"
  - "重新分发 DLL"
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 确定要重新分发的 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在生成由 Visual Studio 提供的 DLL 生成应用程序时，应用程序的用户也必须在其运行该应用程序的计算机上安装这些 DLL。  由于大多数用户可能没有安装 Visual Studio，因此你必须为他们提供这些 DLL。  Visual Studio 以可再发行库的形式提供这些 DLL，因此你将其包含到应用程序的安装程序中。  
  
 这些可再发行 DLL 随 Visual Studio 安装。  默认情况下，他们都安装在 Program Files \(x86\)\\Microsoft Visual Studio version\\VC\\Redist 文件夹中。  若要更轻松地将它们包含到你的安装程序，也可从 Microsoft 下载中心以独立的可再发行组件包形式获得它们。  这些是安装用户的计算机上的可再发行文件的可执行文件。  可再发行组件包的版本必须与创建应用程序的 Visual Studio 工具集的版本相匹配。  若要查找匹配的可再发行组件包，请在 [Microsoft 下载中心](http://go.microsoft.com/fwlink/p/?LinkId=158431)搜索“Visual C\+\+ 可再发行组件包”。  
  
 若要确定必须与应用程序一起重新发布的 DLL，请收集应用程序所依赖的 DLL 列表。  收集该列表的一种方法是运行[了解 Visual C\+\+ 应用程序的依赖项](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)中介绍的依赖项查看器 \(depends.exe\)。  
  
 具有依赖项列表时，将该列表与 Microsoft Visual Studio 安装目录中的所有 Redist.txt 文件中的列表进行比较，或者与你 Visual Studio 版本的 Microsoft 软件许可条款中“可分发代码”部分引用的可再发行 DLL“REDIST 列表”进行比较。  对于 Visual Studio 2013，列表可以在[Microsoft Visual Studio 2013 和 Microsoft Visual Studio 2013 SDK 的可分发代码](http://go.microsoft.com/fwlink/p/?LinkId=313603)中联机获得。  无法重新发布 Visual Studio 中包含的所有文件；只允许重新发布 Redist.txt 或在线“REDIST 列表”中指定的文件。 调试版本的应用程序和各种 Visual C\+\+ 调试 DLL 是不可再发行的。  有关更多信息，请参阅[选择部署方法](../ide/choosing-a-deployment-method.md)。  
  
 下表描述了应用程序可能依赖的一些 Visual C\+\+ DLL。  
  
|Visual C\+\+ 库|描述|适用对象|  
|--------------------|--------|----------|  
|msvcr*version*.dll|面向本机代码的 C 运行库 \(CRT\)。|使用 [CRT 库功能](../c-runtime-library/crt-library-features.md)的应用程序。|  
|msvcp*version*.dll|面向本机代码的标准 C\+\+ 库。|使用[标准 C\+\+ 库](../standard-library/cpp-standard-library-reference.md)的应用程序。|  
|mfc*version*.dll|Microsoft 基础类 \(MFC\) 库。|使用 [MFC 库](../mfc/mfc-desktop-applications.md)的应用程序。|  
|mfc*version*u.dll|具有 Unicode 支持的 MFC 库。|使用 [MFC 库](../mfc/mfc-desktop-applications.md)并需要 Unicode 支持的应用程序。|  
|mfcmifc80.dll|MFC 托管接口库。|使用具有 [Windows 窗体控件](../Topic/Windows%20Forms%20Controls.md)的 [MFC 库](../mfc/mfc-desktop-applications.md)的应用程序。|  
|mfcm*version*.dll|MFC 托管库。|使用具有 [Windows 窗体控件](../Topic/Windows%20Forms%20Controls.md)的 [MFC 库](../mfc/mfc-desktop-applications.md)的应用程序。|  
|mfcm*version*u.dll|具有 Unicode 支持的 MFC 托管库。|使用具有 [Windows 窗体控件](../Topic/Windows%20Forms%20Controls.md)的 [MFC 库](../mfc/mfc-desktop-applications.md)并需要 Unicode 支持的应用程序。|  
  
> [!NOTE]
>  不再需要将活动模板库重新发布为单独的 DLL。  其功能已移至标头和静态库。  
  
 有关如何随应用程序一起重新发布这些 DLL 的更多信息，请参阅[重新分发 Visual C\+\+ 文件](../ide/redistributing-visual-cpp-files.md)。  有关示例，请参阅[部署示例](../ide/deployment-examples.md)。  
  
 通常情况下，无需重新发布系统 DLL，因为它们是操作系统的一部分。  但可能存在例外，例如，当应用程序将在几个版本的 Microsoft 操作系统上运行时。  在这种情况下，请务必阅读相应的许可条款。  此外，请尝试通过 Microsoft 提供的 Windows 更新、Service Pack 或使用可再发行组件包来升级系统 DLL。  你可以通过在 [Microsoft 支持](http://support.microsoft.com/) 网站或 [Microsoft 下载中心](http://go.microsoft.com/fwlink/p/?LinkId=158431) 进行搜索来查找可用的包。  
  
## 请参阅  
 [选择部署方法](../ide/choosing-a-deployment-method.md)   
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)