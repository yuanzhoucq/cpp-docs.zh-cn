---
title: MFC DLL 向导的应用程序设置 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.dll.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a96b166f5fc2873736d01438d91fc971120abf2e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437035"
---
# <a name="application-settings-mfc-dll-wizard"></a>MFC DLL 向导的应用程序设置

MFC DLL 向导的此页用于设计和添加到新的 MFC DLL 项目的基本功能。

## <a name="dll-type"></a>DLL 类型

选择你想要创建的 DLL 的类型。

- **使用的规则 MFC DLL 共享 MFC DLL**

   选择此选项可以链接到你的程序作为共享 DLL 的 MFC 库。 使用此选项，不能在 DLL 和调用应用程序之间共享 MFC 对象。 应用程序在运行时调用的 MFC 库。 如果它组成使用 MFC 库的多个执行文件，此选项可减少您的程序的磁盘和内存要求。 Win32 和 MFC 程序可以在您的 DLL 中调用函数。 必须重新分发 MFC DLL 与此类型的项目。

- **静态链接 mfc 的规则 MFC DLL**

   选择此选项可在程序静态链接到 MFC 库在生成时。 Win32 和 MFC 程序可以在您的 DLL 中调用函数。 虽然此选项会增加您的程序的大小，则不需要重新分发 MFC DLL 与此类型的项目。 您不能在 DLL 和调用应用程序之间共享 MFC 对象。

- **MFC 扩展 DLL**

   如果您希望程序在运行时进行调用的 MFC 库并且你想要共享您的 DLL 和调用应用程序之间的 MFC 对象，请选择此选项。 如果它组成，所有使用 MFC 库的多个可执行文件，此选项可减少应用程序的磁盘和内存要求。 仅 MFC 程序可以在您的 DLL 中调用函数。 必须重新分发 MFC DLL 与此类型的项目。

## <a name="additional-features"></a>其他功能

选择是 MFC DLL 应支持自动化，以及是否它应该支持 Windows 套接字。

- **自动化**

   选择**自动化**允许应用程序操作在另一个程序中实现的对象。 选择**自动化**还会公开给其他自动化客户端应用程序。 请参阅[自动化](../../mfc/automation.md)有关详细信息。

- **Windows 套接字**

   选择此选项以指示您的程序支持 Windows 套接字。 Windows 套接字可以编写通过 TCP/IP 网络进行通信的程序。

   MFC DLL 与 Windows 套接字时创建的支持， [cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)初始化套接字支持，MFC 标头文件 StdAfx.h 包括 AfxSock.h。

## <a name="see-also"></a>请参阅

[MFC DLL 向导](../../mfc/reference/mfc-dll-wizard.md)<br/>
[创建 MFC DLL 项目](../../mfc/reference/creating-an-mfc-dll-project.md)

