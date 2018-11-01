---
title: 从类型库添加 MFC 类
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: 5cd94ad6d400cf2db60131e822f430f87a129cbe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548013"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>从类型库添加 MFC 类

使用此向导创建 MFC 类从可用的类型库中的接口。 可以将 MFC 类添加到 [MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控件](../../mfc/reference/creating-an-mfc-activex-control.md)。

> [!NOTE]
>  不需要使用自动化已启用从类型库添加类创建 MFC 项目。

类型库包含一个组件，定义方法以及其参数和返回类型公开的接口的二进制描述。 必须注册类型库，它才会显示在**可用的类型库**中从类型库向导添加类的列表。 请参阅"在分布式 COM:: 类型库和语言集成"的详细信息的 MSDN library 中。

### <a name="to-add-an-mfc-class-from-a-type-library"></a>若要从类型库添加 MFC 类

1. 在上述**解决方案资源管理器**或[类视图](/visualstudio/ide/viewing-the-structure-of-code)，右键单击你想要将类添加的项目的名称。

1. 从快捷菜单中，单击“添加”，然后单击“添加类”。

1. 在中[添加类](../../ide/add-class-dialog-box.md)对话框中，在模板窗格中，单击**类型库中的 MFC 类**，然后单击**打开**以显示[从类型库向导添加类](../../mfc/reference/add-class-from-typelib-wizard.md).

在向导中，可以添加类型库中的多个类。 同样，您可以将类多个类型库添加单个向导会话中。

该向导创建 MFC 类派生自[COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)，为从选定的类型库中添加每个接口。 `COleDispatchDriver` 实现 OLE 自动化的客户端。

## <a name="see-also"></a>请参阅

[自动化客户端](../../mfc/automation-clients.md)<br/>
[自动化客户端：使用类型库](../../mfc/automation-clients-using-type-libraries.md)

