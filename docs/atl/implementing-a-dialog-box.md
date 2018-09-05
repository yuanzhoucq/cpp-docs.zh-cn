---
title: 实现对话框 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b656af864f8a0dd7c5a69866976b4c1e624b87b9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764288"
---
# <a name="implementing-a-dialog-box"></a>实现对话框

若要添加到 ATL 项目对话框中的两种方式： 使用 ATL 对话框向导或手动添加它。

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>添加 ATL 对话框向导对话框

在中[添加类对话框](../ide/add-class-dialog-box.md)，选择要添加到 ATL 项目对话框中的 ATL 对话框对象。 ATL 对话框向导根据需要填充，然后单击**完成**。 该向导将添加一个类派生自[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)到你的项目。 打开从资源视图**视图**菜单中，找到您的对话框，然后双击它以在资源编辑器中打开它。

> [!NOTE]
>  如果您的对话框派生自`CAxDialogImpl`、 它可以承载这两个 ActiveX 和 Windows 控制。 如果你不希望在对话框类中的 ActiveX 控件支持的系统开销，使用[CSimpleDialog](../atl/reference/csimpledialog-class.md)或[CDialogImpl](../atl/reference/cdialogimpl-class.md)相反。

消息和事件处理程序可以从类视图添加到对话框类。 有关详细信息，请参阅[添加 ATL 消息处理程序](../atl/adding-an-atl-message-handler.md)。

## <a name="adding-a-dialog-box-manually"></a>手动添加一个对话框

实现对话框是类似于实现窗口。 从派生类[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)， [CDialogImpl](../atl/reference/cdialogimpl-class.md)，或[CSimpleDialog](../atl/reference/csimpledialog-class.md) ，并声明[消息映射](../atl/message-maps-atl.md)来处理消息。 但是，还必须指定在派生类中的对话框模板资源 ID。 您的类必须具有一个名为的数据成员`IDD`来保存此值。

> [!NOTE]
>  创建一个对话框使用 ATL 对话框向导时，向导会自动添加`IDD`作为成员**枚举**类型。

`CDialogImpl` 可以实现在安装结束时或承载 Windows 控件的无模式对话框。 `CAxDialogImpl` 可以在安装结束时或无模式对话框承载 ActiveX 和 Windows 控件实现。

若要创建模式对话框，创建的实例在`CDialogImpl`的派生 (或`CAxDialogImpl`-派生) 类，然后调用[DoModal](../atl/reference/cdialogimpl-class.md#domodal)方法。 若要关闭的模式对话框，请调用[EndDialog](../atl/reference/cdialogimpl-class.md#enddialog)从消息处理程序方法。 若要创建无模式对话框，请调用[创建](../atl/reference/cdialogimpl-class.md#create)方法而不是`DoModal`。 若要销毁无模式对话框，请调用[DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow)。

接收器事件中自动完成[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)。 实现对话框的消息处理程序中的处理程序像`CWindowImpl`-派生的类。 如果没有特定于消息的返回值，将其返回为`LRESULT`。 返回`LRESULT`值由 ATL 映射以便进行正确处理由 Windows 对话框管理器。 有关详细信息，请参阅的源代码[CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) atlwin.h 中。

## <a name="example"></a>示例

以下类实现一个对话框：

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>请参阅

[窗口类](../atl/atl-window-classes.md)

