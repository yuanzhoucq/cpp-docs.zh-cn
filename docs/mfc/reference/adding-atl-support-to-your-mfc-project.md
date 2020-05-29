---
title: 向 MFC 项目添加 ATL 支持
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: 05c4e8ba54d9a573b422f136c9e8cf69e48d1c9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371687"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>向 MFC 项目添加 ATL 支持

如果您已经创建了基于 MFC 的应用程序，则可以使用 IDE 轻松添加对活动模板库 （ATL） 的支持。

> [!NOTE]
> 此支持仅适用于添加到 MFC 可执行文件或 DLL 项目的简单 COM 对象。 您可以将其他 COM 对象（包括 ActiveX 控件）添加到 MFC 项目中，但对象可能无法按预期方式运行。

::: moniker range=">=vs-2019"

1. 在解决方案资源管理器中，右键单击项目节点。

1. 在快捷菜单中，依次单击“添加”**** 和“新项”****。

1. 在左侧窗格中选择**ATL，** 然后在中心窗格中选择**ATL 支持**。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-add-atl-support-to-your-mfc-project"></a>将 ATL 支持添加到 MFC 项目

1. 在解决方案资源管理器中，右键单击项目节点。

1. 在快捷菜单上，单击"**添加**"，然后单击"**添加类**"。

1. 在左侧窗格中选择**ATL，** 然后在中心窗格中选择 **"将 ATL 支持添加到 MFC 项目**"。

::: moniker-end

有关添加 ATL 支持如何更改 MFC 项目代码的详细信息，请参阅[ATL 向导添加的 ATL 支持的详细信息](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>另请参阅

[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[导航类结构](../../ide/navigate-code-cpp.md)
