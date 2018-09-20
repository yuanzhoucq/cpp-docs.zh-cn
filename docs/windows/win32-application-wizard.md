---
title: Win32 应用程序向导 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.appwiz.win32.overview
dev_langs:
- C++
helpviewer_keywords:
- Win32 Application Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 26282ef73f6a979cd564bd7597f8418c6535179a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390508"
---
# <a name="win32-application-wizard"></a>Win32 应用程序向导

Visual C++ Win32 应用程序向导，可以创建四种类型中任意一种的项目（在下表中的标题列出）。 在每种情况下，你都可以指定适合于打开项目类型的其他选项。 下表指示了每个应用程序类型可用的选项。

|支持级别|控制台应用程序|可执行 (Windows) 应用程序|动态链接库|静态库|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**空项目**|是|是|是|否|
|**导出符号**|否|否|是|否|
|**预编译头**|否|否|否|是|
|**ATL 支持**|是|No|否|否|
|**MFC 支持**|是|No|否|是|

## <a name="overview"></a>概述

此向导页描述你正在创建的 Win32 应用程序的当前项目设置。 默认设置了以下选项：

- 该项目是 Windows 应用程序。

- 该项目不为空。

- 该项目不包含导出符号。

- 该项目不使用预编译的头文件（此选项仅适用于静态库项目）。

- 该项目不包含对 MFC 和 ATL 的支持。

若要更改这些默认值，请单击向导左列中的 [应用程序设置](../windows/application-settings-win-32-project-wizard.md) 选项卡，并进行所需的更改。

创建 Windows 桌面应用程序后，即可使用 [泛型](../ide/generic-cpp-class-wizard.md) 代码向导添加泛型 C++ 类。 可以添加其他项，例如 HTML 文件、头文件、资源或文本文件。

> [!NOTE]
> 不能添加 ATL 类，只能向支持 MFC 的 Windows 桌面应用程序类型添加 MFC 类（请参阅上表）。

可在 **解决方案资源管理器**中查看你通过向导为项目创建的文件。 向导将创建为你的项目文件的详细信息，请参阅项目生成的文件， `ReadMe.txt`。 有关文件类型的更多信息，请参见 [为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>请参阅

[创建空的 Windows 桌面应用程序](../windows/creating-an-empty-windows-desktop-application.md)<br/>
[Visual C++ 项目类型](../ide/visual-cpp-project-types.md)