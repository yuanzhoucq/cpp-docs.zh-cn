---
title: 添加 ATL 对话框
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: ebbb610debe5d480cd1161149f89c4d357f9cd02
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275789"
---
# <a name="adding-an-atl-dialog-box"></a>添加 ATL 对话框

若要向项目添加 ATL 对话框，你的项目必须是 ATL 项目或包含 ATL 支持的 MFC 项目。 可使用 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或[将 ATL 对象添加到 MFC 应用程序](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现 MFC 应用程序的 ATL 支持。

默认情况下，ATL 对话框向导实现派生自的对话框[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)。 此类包括支持托管 ActiveX 和 Windows 控件。 如果在向导生成代码后不希望 ActiveX 控件支持的系统开销的所有实例替换都为`CAxDialogImpl`带有[CSimpleDialog](../../atl/reference/csimpledialog-class.md)或[CDialogImpl](../../atl/reference/cdialogimpl-class.md)作为基类.

> [!NOTE]
> `CSimpleDialog` 创建仅支持 Windows 公共控件的模式对话框框。 `CDialogImpl` 创建模式对话框或无模式的对话框。

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>若要向项目添加 ATL 对话框资源

1. 创建 ATL 项目使用[ATL 项目向导](../../atl/reference/atl-project-wizard.md)。

1. 从[类视图](/visualstudio/ide/viewing-the-structure-of-code)，右键单击项目名称，然后单击**添加**从快捷菜单。 单击**将类添加**。

1. 在中**模板**窗格[添加类](../../ide/add-class-dialog-box.md)对话框中，单击**ATL 对话框**。 单击**开放**以显示[ATL 对话框向导](../../atl/reference/atl-dialog-wizard.md)。

有关详细信息，请参阅[实现对话框](../../atl/implementing-a-dialog-box.md)。

## <a name="see-also"></a>请参阅

[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[窗口类](../../atl/atl-window-classes.md)<br/>
[消息映射](../../atl/message-maps-atl.md)
