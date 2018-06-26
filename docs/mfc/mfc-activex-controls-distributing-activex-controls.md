---
title: MFC ActiveX 控件： 发行 ActiveX 控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], ANSI or Unicode versions
- RegSvr32.exe
- MFC ActiveX controls [MFC], distributing
- distributing MFC ActiveX controls
- redistributable files, MFC ActiveX controls
- GetSystemDirectory method [MFC]
- registering ActiveX controls
- MSVCRT40.dll
- registry [MFC], registering controls
- LoadLibrary method, registering ActiveX controls
- MFC40U.DLL
- MFC40.DLL
- GetWindowsDirectory method [MFC]
- installing ActiveX controls
- GetProcAddress method, registering ActiveX controls
- MFC ActiveX controls [MFC], installing
- MFC ActiveX controls [MFC], registering
- registering controls
- OLEPRO32.DLL
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d052b2d77df8b3209671b4330347ef642877e47a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928877"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC ActiveX 控件：发行 ActiveX 控件
此文章介绍了相关的重新分发 ActiveX 控件的几个问题：  
  
-   [ANSI 或 Unicode 控件版本](#_core_ansi_or_unicode_control_versions)  
  
-   [安装 ActiveX 控件和可再发行 Dll](#_core_installing_activex_controls_and_redistributable_dlls)  
  
-   [注册控件](#_core_registering_controls)  
  
##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI 或 Unicode 控件版本  
 你必须决定是将该控件，或两个 ANSI 或 Unicode 版本。 此决策基于 ANSI 和 Unicode 字符集中的固有的可移植性因素。  
  
 ANSI 控件，在所有 Win32 操作系统中工作，允许各种 Win32 操作系统之间的最大可移植性。 在仅为 Windows NT （版本 3.51 或更高版本），但不是能在 Windows 95 或 Windows 98 Unicode 控件起作用。 如果你主要关注，随附了 ANSI 控件是可移植性。 如果你的控件将仅在 Windows NT 上运行，你可以将发运 Unicode 控件。 你还可以选择将两者都发布并安装最适合于用户的操作系统版本的应用程序。  
  
##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> 安装 ActiveX 控件和可再发行 Dll  
 安装程序提供使用 ActiveX 控件应创建特殊的 Windows 目录的子目录，并安装的控件的。在其中 OCX 文件。  
  
> [!NOTE]
>  使用 Windows`GetWindowsDirectory`安装程序中的 API 来获取 Windows 目录的名称。 你可能想要从你的公司或产品的名称派生的子目录的名称。  
  
 安装程序必须在 Windows 系统目录中安装所需的可再发行 DLL 文件。 如果任一个 Dll 已存在用户的计算机上，安装程序应比较其版本与要安装的版本。 仅当其版本号高于已安装的文件，重新安装文件。  
  
 可以仅在 OLE 容器应用程序中使用 ActiveX 控件，因为没有无需分发 OLE Dll 与您的控件的完整集。 你可以假定包含应用程序 （或操作系统本身） 具有标准 OLE Dll 安装。  
  
##  <a name="_core_registering_controls"></a> 注册控件  
 可以使用一个控件之前，必须在 Windows 注册数据库中为其创建相应的项。 某些 ActiveX 控件容器提供用户注册新控件的菜单项，但此功能可能不会在所有容器中可用。 因此，您可能希望你的安装程序时才可注册控件。  
  
 如果你愿意，你可以编写你的安装程序以改为直接注册控件。  
  
 使用`LoadLibrary`Windows API 来加载 DLL 的控件。 接下来，使用`GetProcAddress`获取"dllregisterserver 的调用"函数的地址。 最后，调用`DllRegisterServer`函数。 下面的代码示例演示一个可能的方法，其中`hLib`将句柄的控件库中，存储和`lpDllEntryPoint`存储"dllregisterserver 的调用"函数的地址。  
  
 [!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]  
  
 直接注册控件的优点是，你不需要调用，并加载单独的进程 (即 REGSVR32)，从而减少了安装时间。 此外，因为注册是一个内部的过程，安装程序可以处理错误，并且出现未预见的情况下更好外部进程可以。  
  
> [!NOTE]
>  你的安装程序安装 ActiveX 控件之前，则应调用`OleInitialize`。 你的安装程序完成后，调用`OleUnitialize`。 这将确保 OLE 系统 Dll 位于正确的状态以注册 ActiveX 控件。  
  
 你应该注册 MFCx0.DLL。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

