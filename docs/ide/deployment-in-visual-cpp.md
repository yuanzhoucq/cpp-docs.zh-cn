---
title: "Visual C++ 中的部署 | Microsoft Docs"
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
  - "应用程序部署 [C++]"
  - "部署应用程序 [C++]"
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Visual C++ 中的部署
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 应用程序部署到另一台计算机时，必须安装该应用程序和其依赖的任何库文件。  如果库已更新（例如纠正安全漏洞时），你可能要将更新应用到任何部署该应用程序的位置。  
  
 Visual Studio 提供三种方法来部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库以及你的应用程序：集中部署、本地部署和静态链接。  Microsoft 会自动更新集中部署的库。  对于本地部署或静态链接的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库，应用程序编写者必须提供更新。  
  
## 集中部署  
 在集中部署中，[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库文件安装到 %windir%\\system32\\ 目录中。  若要集中部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库，你可以使用以下文件之一：  
  
-   可再发行组件包文件，这是独立的命令行可执行文件，可用于安装 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 可再发行库。  
  
-   可再发行合并模块（.msm 文件），可用于部署特定的库，并且你将其包含在应用程序的 Windows Installer \(.msi\) 文件中。  
  
 可再发行组件包文件将安装特定系统体系结构的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库。  你可以对应用程序的安装文件编程，将其作为安装应用程序前的先决条件予以运行。  合并模块可将特定 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库的安装逻辑包含在 Windows Installer 应用程序的安装文件中。  你可以包含应用程序所要求数量的合并模块。  
  
 由于通过可再发行组件包集中部署的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库可启用 Microsoft 提供的自动更新，所以我们建议你对应用程序使用动态链接和可再发行组件包。  
  
## 本地部署  
 在本地部署中，库文件以及可执行文件安装在应用程序文件夹中。  不同的库版本可安装在同一文件夹中，因为每个版本的文件名都包含其版本号，所以是唯一的。  例如，C 运行时的 12 版本是 msvcr120.dll。  
  
 由于 Microsoft 无法自动更新本地部署的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库，所以我们要警惕这些本地部署的库。  如果你决定使用可再发行库的本地部署，建议你实现自己的自动更新本地部署库的方法。  
  
## 静态链接  
 你可以将 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库静态链接到应用程序（即编译到应用程序中），这样就不必单独部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库文件了。  但是，我们还是要警惕这种方法，因为静态链接的库无法就地更新。  如果你使用静态链接并且希望更新链接的库，则必须重新编译和重新部署应用程序。  
  
## 疑难解答  
 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 库的加载顺序与系统相关。  若要诊断加载程序问题，请使用 depends.exe 或 where.exe。  有关详细信息，请参阅 [Dynamic\-Link Library Search Order \(Windows\)](http://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)（动态链接库搜索顺序 \(Windows\)）。  
  
## 请参阅  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)