---
title: 实现对话框
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 7866afd26c901181f2b4193a87daf5dca2b0c67f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226680"
---
# <a name="implementing-a-dialog-box"></a>实现对话框

可通过两种方法将对话框添加到 ATL 项目：使用 ATL 对话框向导或手动添加。

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>使用 ATL 对话框向导添加对话框

在 "[添加类" 对话框](../ide/add-class-dialog-box.md)中，选择 "Atl" 对话框对象以将对话框添加到 atl 项目。 根据需要填写 ATL 对话框向导，然后单击 "**完成**"。 向导将从[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)派生的类添加到项目。 从 "**视图**" 菜单打开**资源视图**，找到对话框，然后双击以在资源编辑器中打开它。

> [!NOTE]
> 如果对话框是从派生的 `CAxDialogImpl` ，则它可以承载 ActiveX 控件和 Windows 控件。 如果你不想在对话框类中提供 ActiveX 控件支持的开销，请改用[CSimpleDialog](../atl/reference/csimpledialog-class.md)或[CDialogImpl](../atl/reference/cdialogimpl-class.md) 。

消息和事件处理程序可以从类视图添加到对话框类。 有关详细信息，请参阅[添加 ATL 消息处理程序](../atl/adding-an-atl-message-handler.md)。

## <a name="adding-a-dialog-box-manually"></a>手动添加对话框

实现对话框类似于实现窗口。 从[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)、 [CDialogImpl](../atl/reference/cdialogimpl-class.md)或[CSimpleDialog](../atl/reference/csimpledialog-class.md)派生类，并声明[消息映射](../atl/message-maps-atl.md)来处理消息。 但是，还必须在派生类中指定对话框模板资源 ID。 类必须有一个名为的数据成员 `IDD` 来保存此值。

> [!NOTE]
> 使用 ATL 对话框向导创建对话框时，向导会自动将 `IDD` 成员添加为 **`enum`** 类型。

`CDialogImpl`允许实现承载 Windows 控件的模式对话框或无模式对话框。 `CAxDialogImpl`允许实现一个承载 ActiveX 和 Windows 控件的模式对话框或无模式对话框。

若要创建模式对话框，请创建 `CDialogImpl` 派生的（或派生的）类的实例， `CAxDialogImpl` 然后调用[DoModal](../atl/reference/cdialogimpl-class.md#domodal)方法。 若要关闭模式对话框，请从消息处理程序中调用[EndDialog](../atl/reference/cdialogimpl-class.md#enddialog)方法。 若要创建无模式对话框，请调用[create](../atl/reference/cdialogimpl-class.md#create)方法而不是 `DoModal` 。 若要销毁无模式对话框，请调用[DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow)。

接收事件是在[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)中自动完成的。 实现该对话框的消息处理程序，就像派生类中的处理程序一样 `CWindowImpl` 。 如果有特定于消息的返回值，请将其作为返回 `LRESULT` 。 返回 `LRESULT` 值由 ATL 映射，以实现 Windows 对话框管理器的正确处理。 有关详细信息，请参阅 CDialogImplBaseT 的源代码： atlwin.h 中的[ialogproc:D](../atl/reference/cdialogimpl-class.md#dialogproc) 。

## <a name="example"></a>示例

下面的类实现一个对话框：

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>另请参阅

[窗口类](../atl/atl-window-classes.md)
