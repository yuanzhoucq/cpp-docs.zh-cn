---
title: "支持的平台 (Visual C++) | Microsoft Docs"
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
  - " [C++]"
  - "Visual C++, 支持的平台"
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 支持的平台 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 生成的应用程序可以面向各种平台，如下所示。  
  
|操作系统|x86|x64|ARM|  
|----------|---------|---------|---------|  
|Windows XP|X\*|X\*||  
|[!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]|X\*|X\*||  
|Windows Vista|X|X||  
|Windows Server 2008|X|X||  
|Windows 7|X|X||  
|Windows Server 2012 R2|X|X||  
|Windows 8|X|X|X|  
|Windows 8.1|X|X|X|  
|Windows 10|X|X|X|  
|Android \*\*|X|X|X|  
|iOS \*\*|X|X|X|  
  
 \*可以使用 Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012 Update 1 或更高版本中包括的 Windows XP 平台工具集生成 Windows XP 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 项目。  有关如何使用此平台工具集的信息，请参阅[配置适用于 Windows XP 的 C\+\+ 11 程序](../build/configuring-programs-for-windows-xp.md)。  有关更改平台工具集的其他信息，请参阅[如何：修改目标框架和平台工具集](../build/how-to-modify-the-target-framework-and-platform-toolset.md)。  
  
 \*\*可以安装 Visual Studio 2015 安装程序中用于跨平台移动开发的 Visual C\+\+ 可选组件，以面向 iOS 或 Android 平台。  有关说明，请参阅[安装用于跨平台移动开发的 Visual C\+\+](../Topic/Install%20Visual%20C++%20for%20Cross-Platform%20Mobile%20Development.md)。  要生成 iOS 代码，必须拥有 Mac 计算机并满足其他要求。  有关先决条件和安装说明的列表，请参阅[安装并配置使用 iOS 进行生成的工具](../Topic/Install%20And%20Configure%20Tools%20to%20Build%20using%20iOS.md)。  可以生成 x86 或 ARM 代码以匹配目标硬件。  使用 x86 配置以针对 iOS 模拟器、Microsoft Visual Studio Emulator for Android 和某些 Android 设备进行生成。  使用 ARM 配置以针对 iOS 设备和大多数 Android 设备进行生成。  
  
 有关如何设置目标平台配置的信息，请参阅[如何：针对 64 位平台配置 Visual C\+\+ 项目](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)。  
  
## 请参阅  
 [Visual Studio 版本中的 Visual C\+\+ 工具和模板](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md)   
 [Getting Started](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md)