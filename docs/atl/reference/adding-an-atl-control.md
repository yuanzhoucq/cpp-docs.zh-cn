---
title: 添加 ATL 控件
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
ms.openlocfilehash: 836b19cef38549bcdf6cddeeda5bbb7fee08a1c1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298433"
---
# <a name="adding-an-atl-control"></a>添加 ATL 控件

使用此向导将用户界面对象添加到所有潜在容器支持接口的项目。 若要支持这些接口，该项目必须已创建为 ATL 应用程序或作为包含 ATL 支持的 MFC 应用程序。 可使用 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或[将 ATL 对象添加到 MFC 应用程序](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现 MFC 应用程序的 ATL 支持。

## <a name="to-add-an-atl-control-to-your-project"></a>若要向项目添加 ATL 控件

1. 在上述**解决方案资源管理器**或[类视图](/visualstudio/ide/viewing-the-structure-of-code)，右键单击你想要添加的 ATL 简单对象的项目的名称。

1. 单击**外**从快捷菜单，然后单击**添加类**。

1. 在中[添加类](../../ide/add-class-dialog-box.md)对话框中，在模板窗格中，单击**ATL 控件**，然后单击**添加**以显示[ATL 控件向导](../../atl/reference/atl-control-wizard.md)。

使用**ATL 控件向导**，可以创建一个三种类型的控件：

- 标准控件

- 复合控件

- DHTML 控件

此外，可以降低控件的大小和删除未使用的大多数容器通过选择接口**最低限度的控制**上**选项**向导页。

## <a name="see-also"></a>请参阅

[向复合控件添加功能](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)
