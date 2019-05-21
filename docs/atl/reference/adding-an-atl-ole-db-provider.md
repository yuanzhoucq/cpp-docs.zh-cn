---
title: 添加 ATL OLE DB 提供程序
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, adding ATL OLE DB provider to projects
- ATL projects, adding ATL OLE DB providers
- ATL OLE DB providers
ms.assetid: 26fba1e3-880f-4bc6-90e5-2096a48a3a6c
ms.openlocfilehash: 78f26f43d11471c83bf9efcfc3aa55a23f0fbf3e
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524614"
---
# <a name="adding-an-atl-ole-db-provider"></a>添加 ATL OLE DB 提供程序

::: moniker range="vs-2019"

ATL OLE DB 提供程序向导不适用于 Visual Studio 2019 及更高版本。

::: moniker-end

::: moniker range="vs-2017"

此向导可用于将 ATL OLE DB 提供程序添加到项目中。 ATL OLE DB 提供程序由数据源、会话、命令和行集类组成。 项目必须已创建为 ATL COM 应用程序。

## <a name="to-add-an-atl-ole-db-provider-to-your-project"></a>将 ATL OLE DB 提供程序添加到项目中的具体步骤

1. 在“类视图”中，右键单击项目。 在快捷菜单中，依次单击“添加”和“添加类”。

1. 在“Visual C++”文件夹中，双击或选择“ATL OLE DB 提供程序”图标，再单击“打开”。

   此时，ATL OLE DB 提供程序向导打开。

1. 根据 [ATL OLE DB 提供程序向导](../../atl/reference/atl-ole-db-provider-wizard.md)中所述来定义设置。

1. 单击“完成”以关闭向导，这会在项目中插入新创建的 OLE DB 提供程序代码。

::: moniker-end

## <a name="see-also"></a>请参阅

[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)
