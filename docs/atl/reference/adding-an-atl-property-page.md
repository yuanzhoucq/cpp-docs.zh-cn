---
title: 添加 ATL 属性页 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c46adc199a5d6b0bc814cc203b94ac3d268a560d
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860623"
---
# <a name="adding-an-atl-property-page"></a>添加 ATL 属性页

若要添加到你的项目的活动模板库 (ATL) 属性页，项目必须已创建作为 ATL 应用程序或包含 ATL 支持的 MFC 应用程序。 可以使用[ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序或[ATL 对象添加到 MFC 应用程序](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)实现为 MFC 应用程序的 ATL 支持。

如果要添加的控件属性页，控件必须支持[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)接口。 默认情况下，此接口是在控件的派生列表类时您[创建 ATL 控件](../../atl/reference/adding-an-atl-control.md)使用[ATL 控件向导](../../atl/reference/atl-control-wizard.md)。

> [!NOTE]
> 如果你的控件类没有[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)在其派生列表中，您必须手动添加它。

## <a name="to-add-an-atl-property-page-to-your-project"></a>若要向项目添加 ATL 属性页

1. 在上述**解决方案资源管理器**或[类视图](/visualstudio/ide/viewing-the-structure-of-code)，右键单击你想要添加的 ATL 属性页的项目的名称。

1. 从快捷菜单中，单击**外**，然后单击**添加类**。

1. 在中[添加类](../../ide/add-class-dialog-box.md)对话框中**模板**窗格中，单击**ATL 属性页**，然后单击**打开**显示[ATL 属性页向导](../../atl/reference/atl-property-page-wizard.md)。

一旦创建了一个控件的属性页，必须提供[PROP_PAGE](property-map-macros.md#prop_page)控件属性映射中的条目。

## <a name="see-also"></a>请参阅

[属性页](../../atl/atl-com-property-pages.md)<br/>
[ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[示例：实现属性页](../../atl/example-implementing-a-property-page.md)
