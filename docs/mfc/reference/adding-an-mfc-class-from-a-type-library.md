---
title: 从类型库添加 MFC 类
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: bf9c763a215a4880d5b0ad206f6a347341fea9eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371724"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>从类型库添加 MFC 类

使用此向导可以从可用类型库中的接口创建 MFC 类。 可以将 MFC 类添加到 [MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控件](../../mfc/reference/creating-an-mfc-activex-control.md)。

> [!NOTE]
> 无需在启用自动化功能后创建 MFC 项目，即从类型库中添加类。

类型库包含组件公开的接口的二进制描述，定义方法及其参数和返回类型。 必须注册类型库才能显示在"从 Typelib 向导添加类"中的 **"可用类型库**"列表中。 有关详细信息，请参阅 MSDN 库中的"内部分布式 COM：类型库和语言集成"。

### <a name="to-add-an-mfc-class-from-a-type-library"></a>从类型库中添加 MFC 类

1. 在**解决方案资源管理器**或[类视图中](/visualstudio/ide/viewing-the-structure-of-code)，右键单击要向其添加类的项目的名称。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加类**"。

1. 在["添加类"](../../ide/add-class-dialog-box.md)对话框中，在"模板"窗格中，单击**Typelib 中的 MFC 类**，然后单击 **"打开"** 以显示["从 Typelib 向导添加类](../../mfc/reference/add-class-from-typelib-wizard.md)"。

在向导中，可以在类型库中添加多个类。 同样，您可以在单个向导会话中从多个类型库中添加类。

该向导为从所选类型库添加的每个接口创建一个 MFC 类，该类派生自[COleDispatchDriver。](../../mfc/reference/coledispatchdriver-class.md) `COleDispatchDriver`实现 OLE 自动化的客户端。

## <a name="see-also"></a>另请参阅

[自动化客户端](../../mfc/automation-clients.md)<br/>
[自动化客户端：使用类型库](../../mfc/automation-clients-using-type-libraries.md)
