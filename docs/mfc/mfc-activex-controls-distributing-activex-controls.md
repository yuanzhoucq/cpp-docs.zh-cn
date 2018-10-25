---
title: MFC ActiveX 控件： 发行 ActiveX 控件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
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
ms.openlocfilehash: 734707256bb97e25452c45829fd99a1e0fb06fd0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060307"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC ActiveX 控件：发行 ActiveX 控件

本文讨论了与重新分发 ActiveX 控件相关的几个问题：

- [ANSI 或 Unicode 控制版本](#_core_ansi_or_unicode_control_versions)

- [安装 ActiveX 控件和可再发行 Dll](#_core_installing_activex_controls_and_redistributable_dlls)

- [注册控件](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 本文将取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI 或 Unicode 控制版本

您必须决定是否寄送的控件，或两者的 ANSI 或 Unicode 版本。 此决定基于 ANSI 和 Unicode 字符集中固有的可移植性因素。

ANSI 控件，在所有 Win32 操作系统中工作，允许各种 Win32 操作系统之间的最大可移植性。 仅 Windows NT （版本 3.51 或更高版本），但不是在 Windows 95 或 Windows 98 上，Unicode 控件正常工作。 如果可移植性是主要考虑因素，发货 ANSI 控件。 如果您的控件将仅在 Windows NT 上运行，您可以寄送 Unicode 控件。 此外可以进行选择，两者都发布，并让你安装最适合于用户的操作系统版本的应用程序。

##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> 安装 ActiveX 控件和可再发行 Dll

提供使用 ActiveX 控件安装程序应创建特殊 Windows 目录的子目录，并安装控件的。OCX 文件。

> [!NOTE]
>  使用 Windows`GetWindowsDirectory`安装程序中的 API 来获取 Windows 目录的名称。 您可能想要从你的公司或产品的名称派生的子目录名称。

安装程序必须在 Windows 系统目录中安装所需的可再发行 DLL 文件。 如果已存在用户的计算机上的任何 Dll，安装程序应比较其版本和要安装的版本。 仅当其版本号高于已安装的文件，重新安装文件。

由于可以仅在 OLE 容器应用程序中使用 ActiveX 控件，因此没有必要分发 OLE Dll 与您的控件的完整集。 您可以假定包含应用程序 （或操作系统本身） 具有标准 OLE Dll 安装。

##  <a name="_core_registering_controls"></a> 注册控件

可以使用一个控件之前，必须在 Windows 注册数据库中为其创建合适的条目。 某些 ActiveX 控件容器提供用户注册新控件的菜单项，但此功能可能不可用的所有容器中。 因此，您可以注册这些控件，在安装将安装程序。

如果您愿意，可以编写安装程序以改为直接注册控件。

使用`LoadLibrary`Windows API 来加载 DLL 的控件。 接下来，使用`GetProcAddress`获取"DllRegisterServer"函数的地址。 最后，调用`DllRegisterServer`函数。 下面的代码示例演示了一个可能的方法，其中`hLib`存储的句柄的控件库和`lpDllEntryPoint`存储"DllRegisterServer"函数的地址。

[!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

直接注册控件的优点是，您不需要调用并加载一个单独的进程 (即 REGSVR32)，从而减少了安装时间。 此外，注册是一个内部过程，因为安装程序可以处理错误，并且无法预见的情况优于外部进程可以。

> [!NOTE]
>  安装程序安装的 ActiveX 控件之前，它应调用`OleInitialize`。 安装程序完成后，调用`OleUnitialize`。 这可确保 OLE 系统 Dll 位于正确的状态以注册 ActiveX 控件。

你应该注册 MFCx0.DLL。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

