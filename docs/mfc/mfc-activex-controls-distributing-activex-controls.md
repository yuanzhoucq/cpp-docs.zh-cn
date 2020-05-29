---
title: MFC ActiveX 控件：发行 ActiveX 控件
ms.date: 09/12/2018
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
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
ms.openlocfilehash: 1ada1c801b2d9d62f1cc4cd5bf72a2995225b3de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364617"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC ActiveX 控件：发行 ActiveX 控件

本文讨论了与重新分发 ActiveX 控件相关的几个问题：

- [ANSI 或 Unicode 控制版本](#_core_ansi_or_unicode_control_versions)

- [安装 ActiveX 控制和可再分发的 DLL](#_core_installing_activex_controls_and_redistributable_dlls)

- [注册控件](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>ANSI 或 Unicode 控制版本

您必须决定是提供控件的 ANSI 或 Unicode 版本，还是同时发货。 此决策基于 ANSI 和 Unicode 字符集中固有的可移植性因素。

ANSI 控件适用于所有 Win32 操作系统，允许在各种 Win32 操作系统之间实现最大的可移植性。 Unicode 控件仅在 Windows NT（版本 3.51 或更高版本）上工作，但在 Windows 95 或 Windows 98 上不起作用。 如果可移植性是您最关心的问题，请提供 ANSI 控件。 如果控件仅在 Windows NT 上运行，则可以提供 Unicode 控件。 您还可以选择同时发货，并让应用程序安装最适合用户操作系统的版本。

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>安装 ActiveX 控制和可再分发的 DLL

与 ActiveX 控件一起提供的安装程序应创建 Windows 目录的特殊子目录并安装控件的 。OCX 文件。

> [!NOTE]
> 使用安装程序中的`GetWindowsDirectory`Windows API 获取 Windows 目录的名称。 您可能希望从公司或产品的名称派生子目录名称。

安装程序必须在 Windows 系统目录中安装必要的可再分发 DLL 文件。 如果用户的计算机上已存在任何 DLL，安装程序应将其版本与您正在安装的版本进行比较。 仅当文件的版本号高于已安装的文件时，才重新安装该文件。

由于 ActiveX 控件只能在 OLE 容器应用程序中使用，因此无需将完整的 OLE DLL 集与控件一起分发。 可以假定包含的应用程序（或操作系统本身）安装了标准 OLE DLL。

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>注册控件

在使用控件之前，必须在 Windows 注册数据库中为其创建适当的条目。 某些 ActiveX 控件容器为用户提供了一个菜单项，供用户注册新的控件，但此功能可能并非在所有容器中都可用。 因此，您可能希望安装程序在安装控件时注册它们。

如果您愿意，可以编写安装程序以直接注册控件。

使用`LoadLibrary`Windows API 加载控件 DLL。 接下来，使用`GetProcAddress`以获取"DllRegisterServer"功能的地址。 最后，调用函数`DllRegisterServer`。 以下代码示例演示了一种可能的方法，`hLib`其中存储控件库的句柄并`lpDllEntryPoint`存储"DllRegisterServer"函数的地址。

[!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

直接注册控件的优点是，您不需要调用和加载单独的进程（即 REGSVR32），从而减少安装时间。 此外，由于注册是一个内部过程，安装程序可以比外部进程更好地处理错误和不可预见的情况。

> [!NOTE]
> 在安装程序安装 ActiveX 控件之前，它应该调用`OleInitialize`。 安装程序完成后，调用`OleUnitialize`。 这可确保 OLE 系统 DLL 处于注册 ActiveX 控件的适当状态。

您应该注册 MFCx0.DLL。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)
