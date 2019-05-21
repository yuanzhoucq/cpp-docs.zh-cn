---
title: 添加 ATL 属性页
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: 81f793fbdc6d9dda567051b8c35a96f3d3f2f470
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524617"
---
# <a name="adding-an-atl-property-page"></a>添加 ATL 属性页

> [!NOTE] 
> ATL 属性页向导不适用于 Visual Studio 2019 及更高版本。

若要将活动模板库 (ATL) 属性页添加到项目中，项目必须已创建为 ATL 应用程序或支持 ATL 的 MFC 应用程序。 可使用 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，也可以按照[将 ATL 对象添加到 MFC 应用程序](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)中的说明操作，为 MFC 应用程序实现 ATL 支持。

若要为控件添加属性页，控件必须支持 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) 接口。 默认情况下，在你使用 [ATL 控件向导](../../atl/reference/atl-control-wizard.md)[创建 ATL 控件](../../atl/reference/adding-an-atl-control.md)时，此接口位于控件类的派生列表中。

> [!NOTE]
> 如果控件类的派生列表中没有 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)，你必须手动添加它。

## <a name="to-add-an-atl-property-page-to-your-project"></a>向项目添加 ATL 属性页的具体步骤

1. 在“解决方案资源管理器”或[“类视图”](/visualstudio/ide/viewing-the-structure-of-code)中，右键单击要向其添加 ATL 属性页的项目的名称。

1. 在快捷菜单中，依次单击“添加”和“添加类”。

1. 在[“添加类”](../../ide/add-class-dialog-box.md)对话框的“模板”窗格中，依次单击“ATL 属性页”和“打开”来显示 [ATL 属性页向导](../../atl/reference/atl-property-page-wizard.md)。

为控件创建属性页后，必须在属性映射中为控件提供 [PROP_PAGE](property-map-macros.md#prop_page) 条目。

## <a name="see-also"></a>请参阅

[属性页](../../atl/atl-com-property-pages.md)<br/>
[ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[示例：实现属性页](../../atl/example-implementing-a-property-page.md)
