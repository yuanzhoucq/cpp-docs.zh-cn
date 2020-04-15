---
title: 实现对话框
ms.date: 11/04/2016
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
ms.openlocfilehash: 435926b0a0affde03580ceb2b479cb08a17d0454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319478"
---
# <a name="implementing-a-dialog-box"></a>实现对话框

有两种方法可以将对话框添加到 ATL 项目：使用 ATL 对话框向导或手动添加它。

## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>使用 ATL 对话框向导添加对话框

在["添加类"对话框](../ide/add-class-dialog-box.md)中，选择 ATL 对话框对象以向 ATL 项目添加对话框。 根据需要填写 ATL 对话框向导，然后单击 **"完成**"。 该向导将派生自[CAxDialogImpl 的](../atl/reference/caxdialogimpl-class.md)类添加到项目中。 从 **"查看"菜单**打开 **"资源视图**"，找到对话框，然后双击该视图以在资源编辑器中打开它。

> [!NOTE]
> 如果对话框派生自`CAxDialogImpl`，它可以同时承载 ActiveX 和 Windows 控件。 如果不希望对话框类中出现 ActiveX 控件支持的开销，请使用[CSimpleDialog](../atl/reference/csimpledialog-class.md)或[CDialogImpl。](../atl/reference/cdialogimpl-class.md)

可以从类视图将消息和事件处理程序添加到对话框类中。 有关详细信息，请参阅添加[ATL 消息处理程序](../atl/adding-an-atl-message-handler.md)。

## <a name="adding-a-dialog-box-manually"></a>手动添加对话框

实现对话框类似于实现窗口。 从[CAxDialogImpl、CDialogImpl](../atl/reference/caxdialogimpl-class.md)[CDialogImpl](../atl/reference/cdialogimpl-class.md)或[CSimpleDialog](../atl/reference/csimpledialog-class.md)派生一个类，并声明[消息映射](../atl/message-maps-atl.md)来处理消息。 但是，还必须在派生类中指定对话框模板资源 ID。 类必须具有调用`IDD`的数据成员才能保存此值。

> [!NOTE]
> 使用 ATL 对话框向导创建对话框时，向导会自动将`IDD`成员添加为**枚举**类型。

`CDialogImpl`允许您实现承载 Windows 控件的模式或无模式对话框。 `CAxDialogImpl`允许您实现承载 ActiveX 和 Windows 控件的模式或无模式对话框。

要创建模态对话框，请创建`CDialogImpl`派生（或`CAxDialogImpl`派生）类的实例，然后调用[DoModal](../atl/reference/cdialogimpl-class.md#domodal)方法。 要关闭模式对话框，请从消息处理程序调用[EndDialog](../atl/reference/cdialogimpl-class.md#enddialog)方法。 要创建无模式对话框，请调用[Create](../atl/reference/cdialogimpl-class.md#create)方法而不是`DoModal`。 要销毁无模式对话框，请调用["销毁窗口](../atl/reference/cdialogimpl-class.md#destroywindow)"。

下沉事件在[CAxDialogImpl 中](../atl/reference/caxdialogimpl-class.md)自动完成。 实现对话框的消息处理程序，就像派生类中的处理程序一`CWindowImpl`样。 如果有特定于消息的返回值，则将其作为 返回。 `LRESULT` 返回`LRESULT`的值由 ATL 映射，以便 Windows 对话框管理器正确处理。 有关详细信息，请参阅 atlwin.h 中的[CDialogImplBaseT：:DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc)的源代码。

## <a name="example"></a>示例

以下类实现一个对话框：

[!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]

## <a name="see-also"></a>另请参阅

[窗口类](../atl/atl-window-classes.md)
