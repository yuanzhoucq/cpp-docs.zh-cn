---
title: ATL 向导添加的 ATL 支持的详细信息
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: 2651a83c50b03dfffd1ac0238b6c6d0a61888c88
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66741555"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>ATL 向导添加的 ATL 支持的详细信息

时您[将 ATL 支持添加到现有的 MFC 可执行文件或 DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)、 VisualC++进行以下修改现有 MFC 项目 (在此示例中，该项目称为`MFCEXE`):

- 添加两个新文件 （.idl 文件和.rgs 文件中，用来注册服务器）。

- 在主应用程序标头和实现文件 （Mfcexe.h 和 Mfcexe.cpp） 的新类 (派生自`CAtlMFCModule`) 添加。 除了新的类，代码添加到`InitInstance`进行注册。 代码还将添加到`ExitInstance`吊销类对象的函数。 在标头文件中，最后，两个新标头文件 （Initguid.h 和 Mfcexe_i.c） 包含在实现文件中，声明和初始化的新 Guid `CAtlMFCModule`-派生的类。

- 若要正确注册的服务器，将新的 rgs 文件的条目添加到项目的资源文件。

## <a name="notes-for-dll-projects"></a>DLL 项目的说明

向非 MFC DLL 项目添加 ATL 支持，您将看到一些差异。 代码添加到`DLLRegisterServer`和`DLLUnregisterServer`用于注册和注销该 DLL 的函数。 代码还将添加到[DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow)并[DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject)。

## <a name="see-also"></a>请参阅

[MFC 项目中的 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[导航类结构](../../ide/navigate-code-cpp.md)
