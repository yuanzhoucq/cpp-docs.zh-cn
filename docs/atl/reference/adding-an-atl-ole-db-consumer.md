---
title: 添加 ATL OLE DB 使用者
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- OLE DB, adding ATL OLE DB consumer to projects
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
ms.openlocfilehash: d93bf715f8fd8a03c75b1d1bf2e44f12c1d1b9c0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277646"
---
# <a name="adding-an-atl-ole-db-consumer"></a>添加 ATL OLE DB 使用者

使用此向导以向项目添加 ATL OLE DB 使用者。 ATL OLE DB 使用者包含 OLE DB 访问器类和数据绑定访问数据源所必需。 为 ATL COM 应用程序，或包含 ATL 支持 （它会自动添加 ATL OLE DB 使用者向导） 的 MFC 或 Win32 应用程序，该项目必须已创建。

> [!NOTE]
> 可以向 MFC 项目添加 OLE DB 使用者。 如果这样做，在 ATL OLE DB 使用者向导会将必要的 COM 支持添加到你的项目。 这假定在您创建 MFC 项目，则选择**ActiveX 控件**复选框 (在**高级功能**MFC 项目应用程序向导页)，这默认选中的。 选择此选项可确保应用程序调用`CoInitialize`和`CoUninitialize`。 如果未选中**ActiveX 控件**时创建 MFC 项目，您需要调用`CoInitialize`和`CoUninitialize`主代码中。

## <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>若要向项目添加 ATL OLE DB 使用者

1. 在中**类视图**，右键单击该项目。 在快捷菜单上，单击**外**，然后单击**添加类**。

1. 在 Visual c + + 文件夹中，双击**ATL OLE DB 使用者**图标或选择它，然后单击**打开**。

   ATL OLE DB 使用者向导随即打开。

1. 定义设置，如中所述[ATL OLE DB 使用者向导](../../atl/reference/atl-ole-db-consumer-wizard.md)。

1. 单击**完成**以关闭向导。 将在项目中插入新创建的 OLE DB 使用者代码。

## <a name="see-also"></a>请参阅

[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)
