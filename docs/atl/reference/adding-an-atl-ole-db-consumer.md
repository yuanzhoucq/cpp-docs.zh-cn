---
title: 添加 ATL OLE DB 使用者
ms.date: 05/09/2019
helpviewer_keywords:
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
ms.openlocfilehash: 7925063e03522c96d251748b23b6b929733999a1
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524640"
---
# <a name="adding-an-atl-ole-db-consumer"></a>添加 ATL OLE DB 使用者

::: moniker range="vs-2019"

ATL OLE DB 使用者向导不适用于 Visual Studio 2019 及更高版本。 但仍可以手动添加此功能。 有关详细信息，请参阅[不使用向导创建使用者](../../data/oledb/creating-a-consumer-without-using-a-wizard.md)。

::: moniker-end

::: moniker range="vs-2017"

此向导可用于将 ATL OLE DB 使用者添加到项目中。 ATL OLE DB 使用者由访问数据源所需的 OLE DB 取值函数类和数据绑定组成。 项目必须已创建为 ATL COM 应用程序，或支持 ATL（ATL OLE DB 使用者向导自动添加此支持）的 MFC 或 Win32 应用程序。

> [!NOTE]
> 可以将 OLE DB 使用者添加到 MFC 项目中。 如果你这样做，ATL OLE DB 使用者向导会将必要的 COM 支持添加到项目中。 这假定在创建 MFC 项目时你已选中“ActiveX 控件”复选框（位于 MFC 项目应用程序向导的“高级功能”页中），此框默认处于选中状态。 选中此选项可确保应用程序调用 `CoInitialize` 和 `CoUninitialize`。 如果在创建 MFC 项目时未选中“ActiveX 控件”，必须在主代码中调用 `CoInitialize` 和 `CoUninitialize`。

## <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>将 ATL OLE DB 使用者添加到项目中的具体步骤

1. 在“类视图”中，右键单击项目。 在快捷菜单中，依次单击“添加”和“添加类”。

1. 在“Visual C++”文件夹中，双击或选择“ATL OLE DB 使用者”图标，并单击“打开”。

   此时，ATL OLE DB 使用者向导打开。

1. 根据 [ATL OLE DB 使用者向导](../../atl/reference/atl-ole-db-consumer-wizard.md)中所述来定义设置。

1. 单击“完成”以关闭向导。 此时，新创建的 OLE DB 使用者代码将插入项目中。

::: moniker-end

## <a name="see-also"></a>请参阅

[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)
