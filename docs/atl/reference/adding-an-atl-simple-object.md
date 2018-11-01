---
title: 添加 ATL 简单对象
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding.atl
helpviewer_keywords:
- ATL projects, adding objects
- objects [ATL]
- ATL, simple objects
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
ms.openlocfilehash: df835b35bb036086382fc6adb4beed142f99be76
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508287"
---
# <a name="adding-an-atl-simple-object"></a>添加 ATL 简单对象

若要向项目添加 ATL （动态模板库） 对象，你的项目必须已创建作为 ATL 应用程序或包含 ATL 支持的 MFC 应用程序。 可使用 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或[将 ATL 对象添加到 MFC 应用程序](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现 MFC 应用程序的 ATL 支持。

首先创建它，或更高版本使用添加时，可以为新的 ATL 对象定义 COM 接口[实现接口](../../ide/implement-interface-wizard.md)命令**类视图**快捷菜单。

## <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>若要向 ATL COM 项目添加 ATL 简单对象

1. 在上述**解决方案资源管理器**或[类视图](/visualstudio/ide/viewing-the-structure-of-code)，右键单击你想要添加的 ATL 简单对象的项目的名称。

1. 从快捷菜单中，单击“添加”，然后单击“添加类”。

1. 在中[添加类](../../ide/add-class-dialog-box.md)对话框中**模板**窗格中，单击**ATL 简单对象**，然后单击**打开**显示[ATL 简单对象向导](../../atl/reference/atl-simple-object-wizard.md)。

1. 在设置为你的项目的其他选项[选项](../../atl/reference/options-atl-simple-object-wizard.md)页**ATL 简单对象**向导。

1. 单击**完成**将该对象添加到你的项目。

## <a name="see-also"></a>请参阅

[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[在 ATL 项目中添加新接口](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[将连接点添加到对象](../../atl/adding-connection-points-to-an-object.md)<br/>
[添加方法](../../ide/adding-a-method-visual-cpp.md)<br/>
[MFC 类](../../mfc/reference/adding-an-mfc-class.md)<br/>
[添加一般 C++ 类](../../ide/adding-a-generic-cpp-class.md)
