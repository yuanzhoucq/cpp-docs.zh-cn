---
title: "MFC ActiveX 控件：发行 ActiveX 控件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetWindowsDirectory"
  - "GetSystemDirectory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "分布 MFC ActiveX 控件"
  - "GetProcAddress 方法, 注册 ActiveX 控件"
  - "GetSystemDirectory 方法"
  - "GetWindowsDirectory 方法"
  - "安装 ActiveX 控件"
  - "LoadLibrary 方法, 注册 ActiveX 控件"
  - "MFC ActiveX 控件, ANSI 或 Unicode 版本"
  - "MFC ActiveX 控件, 分发"
  - "MFC ActiveX 控件, 安装"
  - "MFC ActiveX 控件, 注册"
  - "MFC40.DLL"
  - "MFC40U.DLL"
  - "MSVCRT40.dll"
  - "OLEPRO32.DLL"
  - "可再发行字段, MFC ActiveX 控件"
  - "注册 ActiveX 控件"
  - "注册控件"
  - "注册表, 注册控件"
  - "RegSvr32.exe"
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# MFC ActiveX 控件：发行 ActiveX 控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文讨论相关的若干问题。重新发布 ActiveX 控件：  
  
-   [ANSI 或 Unicode 版本控件](#_core_ansi_or_unicode_control_versions)  
  
-   [安装 ActiveX DLL 和可再发行控件](#_core_installing_activex_controls_and_redistributable_dlls)  
  
-   [注册控件](#_core_registering_controls)  
  
    > [!NOTE]
    >  有关重新发布 ActiveX 控件的更多信息，请参见 [重新分布控件](../data/ado-rdo/redistributing-controls.md)。  
  
##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI 或 Unicode 版本控件  
 您必须决定是控件的 ANSI 或 Unicode 版本或者为二者。  此决策基于可移植性因素内部在 ANSI 与 Unicode 字符集。  
  
 ANSI 控件，Win32 研究院具有操作系统，在 Win32 允许各种操作系统之间的最大可移植。  Unicode 控件可以在仅 Windows NT \(版本 3.51 或更高版本\)，但不能在 Windows 95 或 Windows 98\)  可移植性如果是的主要关注，则支持 ANSI 控件。  如果控件在 Windows NT 中只运行，可以支持 Unicode 控件。  您还可能选择发布和安装应用安装最适当的生成对于用户的操作系统。  
  
##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> 安装 ActiveX DLL 和可再发行控件  
 您提供的 ActiveX 控件安装程序应该创建 Windows 目录的一个子目录中安装该控件的特殊和 .ocx 文件。  
  
> [!NOTE]
>  使用 Windows API **GetWindowsDirectory** 在安装程序获取 Windows 目录的名称。  您可能要从的公司或产品名称派生子目录的名称。  
  
 安装程序必须安装在 Windows 系统目录所需 DLL 的可再发行文件。  如果任何 DLL 已经在用户的计算机，安装程序应该比较它们与已安装的版本。  当其版本号高于已安装的文件，请重新安装该文件。  
  
 由于 ActiveX 控件在 OLE 容器应用程序只能使用，不需要完全发布设置与 OLE 控件的 DLL。  可以假定，包含的应用程序 \(或操作系统\) 的标准 OLE DLL 安装。  
  
##  <a name="_core_registering_controls"></a> 注册控件  
 才能使用控件，必须为其创建相应的项。Windows 注册数据库。  数组 ActiveX 控件容器为用户提供一菜单项注册新的控件，但是，此功能可能不可用在任何容器。  因此，但安装时，您可能安装程序注册控件。  
  
 如果您愿意，可直接写入安装程序注册控件。  
  
 使用 Windows 控件 API **LoadLibrary** 加载 DLL。  接下来，使用 **GetProcAddress** 获取“DllRegisterServer”函数的地址。  最后，调用 `DllRegisterServer` 函数。  下面的代码示例演示一种可能的方法，`hLib` 存储了控件库的句柄和 `lpDllEntryPoint` 存储“DllRegisterServer”函数的地址。  
  
 [!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/CPP/mfc-activex-controls-distributing-activex-controls_1.cpp)]  
  
 Register 控件的直接优点是您不需要调用并将单独处理 \(即，REGSVR32\)，减小安装时间。  此外，由于注册，是内部进程，安装程序的外部进程中可以更好地处理错误以及无法预料的情况。  
  
> [!NOTE]
>  在安装程序安装 ActiveX 控件之前，应调用 **OleInitialize**。  当安装程序完成时，请调用 **OleUnitialize**。  这确保 OLE DLL 系统中注册的 ActiveX 控件正确的状态。  
  
 应注册和类。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)