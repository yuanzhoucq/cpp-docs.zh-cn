---
title: 从类型库添加 MFC 类
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: 4e8d0f74a73048f172a8030d4bfb081c803e7170
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405112"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>从类型库添加 MFC 类

使用此向导可以在可用类型库的接口中创建 MFC 类。 可以将 MFC 类添加到 [MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控件](../../mfc/reference/creating-an-mfc-activex-control.md)。

> [!NOTE]
> 无需创建启用了自动化的 MFC 项目，即可从类型库添加类。

类型库包含由组件公开的接口的二进制说明，同时定义方法以及参数和返回类型。 必须注册类型库，才能将其显示在 "从 Typelib 添加类" 向导中的 "**可用类型库**" 列表中。

### <a name="to-add-an-mfc-class-from-a-type-library"></a>从类型库添加 MFC 类

1. 在 "**解决方案资源管理器**" 或 "[类视图](/visualstudio/ide/viewing-the-structure-of-code)中，右键单击要向其添加类的项目的名称。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加类**"。

1. 在 "[添加类](../../ide/add-class-dialog-box.md)" 对话框的 "模板" 窗格中，单击 "**类型库中的 MFC 类**"，然后单击 "**打开**" 以显示 "[从 typelib 添加类" 向导](../../mfc/reference/add-class-from-typelib-wizard.md)。

在向导中，您可以在一个类型库中添加多个类。 同样，您可以在单个向导会话中从多个类型库添加类。

向导将从所选类型库中为添加的每个接口创建一个派生自[COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)的 MFC 类。 `COleDispatchDriver`实现 OLE 自动化的客户端。

## <a name="see-also"></a>另请参阅

[自动化客户端](../../mfc/automation-clients.md)<br/>
[自动化客户端：使用类型库](../../mfc/automation-clients-using-type-libraries.md)
