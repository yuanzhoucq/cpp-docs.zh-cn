---
title: "配置适用于 Windows XP 的 C++ 11 程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
caps.latest.revision: 14
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 配置适用于 Windows XP 的 C++ 11 程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

因为 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 支持多个平台工具集，所以你可以面向不受默认工具集支持的操作系统和运行时库。  例如，可以使用 C\+\+11 语言增强功能、编译器、库以及 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中实现的其他功能，以便创建面向 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 的应用程序。  你可以使用较旧的平台工具集来维护二进制兼容旧代码，同时仍然可以利用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 的最新功能。  
  
> [!NOTE]
>  为了将 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] 和 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 的平台工具集支持添加到 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]，你必须安装 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] Update 4。  若要下载并安装 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] Update 4 的副本，请参阅 Microsoft 下载中心的 [Microsoft Visual Studio Express 2012 for Windows Desktop](http://go.microsoft.com/fwlink/?LinkID=265464)。  然后安装 [Visual Studio 2012 Update 4](http://go.microsoft.com/fwlink/?LinkID=335900) 以获取 v110\_xp 平台工具集。  安装完成后，使用 Windows Update 接收最新的软件更新。  
  
## Windows XP 定向体验  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中内含的 Windows XP 平台工具集是 [!INCLUDE[win7](../build/includes/win7_md.md)] 中内含的 [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)] SDK 的一个版本，但它使用当前的 C\+\+ 编译器。  它还将项目属性配置为适当的默认值，例如，为低级别的定向规范兼容的链接器。  只有通过使用 Windows XP 平台工具集创建的 Windows 桌面应用程序能在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上运行，但这些应用程序也可以在更新的操作系统（如 Windows Vista、[!INCLUDE[win7](../build/includes/win7_md.md)]、[!INCLUDE[winsvr08](../build/includes/winsvr08_md.md)]、[!INCLUDE[win8](../build/includes/win8_md.md)] 或 [!INCLUDE[winserver8](../build/includes/winserver8_md.md)]）上运行。  
  
#### 若要针对 Windows XP  
  
1.  在**“解决方案资源管理器”**中，打开项目的快捷菜单，然后选择**“属性”**。  
  
2.  在项目的“属性页”对话框中，在“配置属性”、“常规”下，将“平台工具集”属性设置为所需的 Windows XP 工具集。  例如，选择“Visual Studio 2012 – Windows XP \(v110\_xp\)”来创建与 Microsoft Visual c\+\+ 2012 可再发行库二进制兼容的代码。  
  
### C\+\+ 运行时支持  
 Windows XP 平台工具集、C 运行库 \(CRT\)、标准模板库 \(STL\)、活动模板库 \(ATL\)、并发运行时库 \(ConCRT\)、并行模式库 \(PPL\)、Microsoft 基础类库 \(MFC\) 和 C\+\+ AMP（C\+\+ 加速大规模编程）库均包括对 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 的运行时支持。  对于这些操作系统，支持的版本是适用于 x86 的 [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 3 \(SP3\)、适用于 x64 的 [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 2 \(SP2\) 以及适用于 x86 和 x64 的 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Service Pack 2 \(SP2\)。  
  
 这些库受由 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 安装的平台工具集的支持，具体取决于目标：  
  
|库|面向 Windows 桌面应用程序的默认平台工具集|面向 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用程序的默认平台工具集|面向 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 的 Windows XP 平台工具集|  
|-------|-------------------------------|---------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|  
|CRT|X|X|X|  
|STL|X|X|X|  
|ATL|X|X|X|  
|ConCRT\/PPL|X|X|X|  
|MFC|X||X|  
|C\+\+ AMP|X|X||  
  
> [!NOTE]
>  用 C\+\+\/CLI 编写且面向 .NET Framework 4 的应用程序在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上运行。  
  
### 工具集之间的差异  
 由于平台和库支持的不同，使用 Windows XP 平台工具集的应用程序的开发体验不及使用默认的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 平台工具集的应用程序完整。  
  
-   **C\+\+ 语言功能**  
  
     在使用 v110\_xp 平台工具集的应用程序中仅支持在 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] 中实现的 C\+\+11 语言功能。  在使用 v120\_xp 平台工具集的应用程序中仅支持在 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] 中实现的 C\+\+ 11 语言功能。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 在使用较旧的平台工具集进行生成时使用相应的编译器。  请使用较新的 Windows XP 平台工具集以利用在该版本中实现的其他 C\+\+11 功能。  
  
-   **远程调试**  
  
     适用于 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的远程工具不支持在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上进行远程调试。  若要在应用程序在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上运行时对其进行调试，可使用来自 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 较早版本的调试器以本地或远程方式对其进行调试。  这类似于调试 Windows Vista 上的应用程序的体验，因为它是平台工具集的运行时目标，而不是远程调试的目标。  
  
-   **静态分析**  
  
     Windows XP 平台工具集不支持静态分析，因为 [!INCLUDE[win7](../build/includes/win7_md.md)] SDK 的 SAL 批注和运行时库不兼容。  如果想对支持 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 的应用程序执行静态分析，可以临时将解决方案切换为针对目标默认平台工具集来进行分析，然后再切换回 Windows XP 平台工具集来构建应用程序。  
  
-   **调试 DirectX 图形**  
  
     因为图形调试器不支持 Direct3D 9 API，所以它不能用于调试在 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 或 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 上使用 Direct3D 的应用程序。  但是，如果应用程序可实现使用 Direct3D 10 或 Direct3D 11 API 的备用呈现器，则可以使用图形调试器来诊断有关这些 API 的使用情况的问题。  
  
-   **正在生成 HLSL**  
  
     默认情况下，Windows XP 工具集不编译 HLSL 源代码文件。  若要编译 HLSL 文件，请下载并安装 2010 年 6 月发行的 DirectX SDK，然后设置项目的 VC 目录以将其包含在内。  有关详细信息，请参阅 [2010 年 6 月 DirectX SDK 下载页](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812)的“DirectX SDK 不用 Visual Studio 2010 注册 Include\/Library 路径”部分。