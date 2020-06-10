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
ms.openlocfilehash: 11d647922a4f8097e03e112c0c93c833524c2c4e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618204"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC ActiveX 控件：发行 ActiveX 控件

本文讨论了与重新发布 ActiveX 控件相关的几个问题：

- [ANSI 或 Unicode 控制版本](#_core_ansi_or_unicode_control_versions)

- [安装 ActiveX 控件和可再发行 Dll](#_core_installing_activex_controls_and_redistributable_dlls)

- [注册控件](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>ANSI 或 Unicode 控制版本

您必须决定是要交付还是同时发送 ANSI 或 Unicode 版本的控件。 此决定基于 ANSI 和 Unicode 字符集固有的可移植性因素。

ANSI 控件适用于所有 Win32 操作系统，允许在各种 Win32 操作系统之间实现最大的可移植性。 Unicode 控制仅适用于 Windows NT （3.51 版或更高版本），但不适用于 Windows 95 或 Windows 98。 如果你主要关注便携性，请发送 ANSI 控件。 如果控件将仅在 Windows NT 上运行，则可以发送 Unicode 控件。 你还可以选择提供，并让你的应用程序安装最适合用户操作系统的版本。

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>安装 ActiveX 控件和可再发行 Dll

您在 ActiveX 控件中提供的安装程序应创建 Windows 目录的特殊子目录并安装控件。文件中的文件。

> [!NOTE]
> 使用 `GetWindowsDirectory` 安装程序中的 windows API 获取 windows 目录的名称。 你可能想要从你的公司或产品名称派生子目录名称。

安装程序必须在 Windows 系统目录中安装所需的可再发行的 DLL 文件。 如果用户的计算机上已存在任何 Dll，则安装程序应将其版本与要安装的版本进行比较。 仅当文件的版本号高于已安装的文件时才重新安装该文件。

由于 ActiveX 控件只能在 OLE 容器应用程序中使用，因此无需将整套 OLE Dll 与控件一起分发。 可以假设包含应用程序（或操作系统本身）安装了标准 OLE Dll。

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>注册控件

在可以使用控件之前，必须在 Windows 注册数据库中为其创建相应的项。 某些 ActiveX 控件容器为用户提供了用于注册新控件的菜单项，但此功能可能在所有容器中都不可用。 因此，你可能希望你的安装程序在安装时注册控件。

如果需要，可以编写安装程序以直接注册控件。

使用 `LoadLibrary` WINDOWS API 加载控件 DLL。 接下来，使用 `GetProcAddress` 获取 "DllRegisterServer" 函数的地址。 最后，调用 `DllRegisterServer` 函数。 下面的代码示例演示了一种可能的方法，其中 `hLib` 存储了控件库的句柄，并 `lpDllEntryPoint` 存储了 "DllRegisterServer" 函数的地址。

[!code-cpp[NVC_MFC_AxCont#16](codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

直接注册控件的优点是不需要调用和加载单独的进程（即 REGSVR32），从而减少了安装时间。 此外，由于注册是一个内部过程，因此安装程序可以处理错误和无法预料的情况，这种情况比外部进程更好。

> [!NOTE]
> 安装程序安装 ActiveX 控件之前，应调用 `OleInitialize` 。 安装程序完成后，调用 `OleUnitialize` 。 这可确保 OLE 系统 Dll 处于正确的状态，以便注册 ActiveX 控件。

应注册 MFCx0。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)
