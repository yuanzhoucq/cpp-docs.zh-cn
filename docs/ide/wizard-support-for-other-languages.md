---
title: "其他语言的向导支持 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.EastAsianLanguages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC 项目的语言支持"
  - "项目 [C++], 语言支持"
  - "向导 [C++], 语言支持"
ms.assetid: b653c673-0687-455c-885f-15d7e2f4149d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 其他语言的向导支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当安装 Visual Studio 时，安装应用程序检测系统中列出的区域设置并为该区域设置安装相应的语言模板。  例如，对于西欧区域设置，安装程序安装英语、法语、意大利语、西班牙语和德语。  这些语言出现在 MFC 应用程序向导的[应用程序类型](../mfc/reference/application-type-mfc-application-wizard.md)页上的“资源语言”列表中。  
  
## 语言模板  
 因为模板基于 ANSI 编码，所以并非所有模板都安装在所有系统上，而且并非所有资源都能在所有系统上进行编辑。  例如，默认情况下，不能在法文系统上编辑日文资源。  
  
 如果您使用的是 Windows 2000 或更高版本，并且要用另一种语言创建 MFC 应用程序，则必须将相应语言的模板目录从 Visual Studio 安装程序介质（光盘 1）复制到您的系统中。  
  
> [!NOTE]
>  要编辑已创建的项目，必须将系统区域设置设置为选定语言的相应区域设置。  
  
 如下表中所示，为每一模板在 \\Microsoft Visual Studio .NET 2003\\Vc7\\VCWizards\\mfcappwiz\\templates\\ 目录中分配了文件夹。  若要访问所需的语言模板，请将相应的文件夹复制到计算机上的 \\mfcappwiz\\templates\\ 目录。  复制了文件夹后，语言将出现在 MFC 应用程序向导的**“应用程序类型”**页上的**“资源语言”**列表中。  
  
### Visual Studio .NET 中提供的语言模板  
  
|Language|模板|  
|--------------|--------|  
|中文\(繁体\)|1028|  
|中文\(简体\)|2052|  
|英语|1033|  
|法语|1036|  
|德语|1031|  
|意大利语|1040|  
|日语|1041|  
|朝鲜语|1042|  
|西班牙语|3082|  
  
## Visual C\+\+ 向导生成的文件的格式  
 当安装的 Visual Studio 语言版本与系统的区域设置不匹配时，Visual C\+\+ 向导将生成 Unicode 项目。  例如，如果一台计算机上安装了日文版的 Visual Studio，而其区域设置为日语以外的其他任何语言，那么 Visual C\+\+ 向导将生成由 Unicode 文件组成的项目。  这在安装了 Windows 多语言 \(MUI\) 包的计算机上很普遍。  
  
 此行为与系统安装的不同之处在于，系统区域设置与 Visual Studio 的语言版本相同。  在这种情况下，将创建 ANSI 系统代码页格式的项目文件。  
  
## 请参阅  
 [为 Visual C\+\+ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [创建和管理 Visual C\+\+ 项目](../ide/creating-and-managing-visual-cpp-projects.md)