---
title: ATL 向导添加的 ATL 支持的详细信息
ms.date: 08/20/2019
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: 10bafc9bd06ee94398f91d5af478a6e1cd7ca617
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108457"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>ATL 向导添加的 ATL 支持的详细信息

::: moniker range=">=vs-2019"

[将 ATL 支持添加到现有 MFC 可执行文件或 DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)时, Visual Studio 会在默认情况下添加一个名为 "*框架*" `#include`的`#define`头文件, 其中包含用于在项目中启用 ATL 的预处理器指令。 不会添加任何其他文件或类, 正如在以前版本的 Visual Studio 中所做的那样。

::: moniker-end

::: moniker range="<=vs-2017"

向[现有 mfc 可执行文件或 DLL 添加 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)时, Visual Studio 将对现有 mfc 项目进行以下修改 (在本示例中, 调用`MFCEXE`项目):

- 添加了两个新文件 (一个用于注册服务器的 .idl 文件和一个 .rgs 文件)。

- 在主应用程序头文件和实现文件 (Mfcexe 和 Mfcexe) 中, 添加了一个新类 (派生自`CAtlMFCModule`)。 除了新类之外, 还会向注册添加`InitInstance`代码。 还会将代码添加到`ExitInstance`用于撤消类对象的函数。 在头文件中, 最后两个新头文件 (initguid.h 和 Mfcexe_i) 包含在实现文件中, 为`CAtlMFCModule`派生类声明并初始化新的 guid。

- 若要正确注册服务器, 请将新的 .rgs 文件条目添加到项目的资源文件中。

::: moniker-end

## <a name="notes-for-dll-projects"></a>DLL 项目说明

向 MFC DLL 项目添加 ATL 支持时, 你将看到一些不同之处。 向`DLLRegisterServer` 和`DLLUnregisterServer`函数添加代码, 用于注册和注销 DLL。 还将代码添加到[DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow)和[DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject)中。

## <a name="see-also"></a>请参阅

[MFC 项目中的 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[导航类结构](../../ide/navigate-code-cpp.md)
