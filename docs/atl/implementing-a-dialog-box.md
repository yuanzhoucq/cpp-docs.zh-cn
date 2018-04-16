---
title: "实现一个对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9b3ff0e58623a241160da21266d085753be1c457
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-a-dialog-box"></a>实现一个对话框
有两种方法将添加到你的 ATL 项目对话框中： 使用 ATL 对话框向导或手动添加它。  
  
## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>添加一个带有 ATL 对话框向导对话框  
 在[添加类对话框](../ide/add-class-dialog-box.md)，选择要添加到你的 ATL 项目的对话框中的 ATL 对话框对象。 填写根据 ATL 对话框向导并单击**完成**。 该向导将添加派生自的类[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)到你的项目。 打开资源视图从**视图**菜单上，找到你的对话框，并双击它以在资源编辑器中打开它。  
  
> [!NOTE]
>  如果对话框中派生自`CAxDialogImpl`、 它可以承载这两个 ActiveX 和 Windows 控制。 如果你不希望在对话框类中的 ActiveX 控件支持的开销，使用[CSimpleDialog](../atl/reference/csimpledialog-class.md)或[CDialogImpl](../atl/reference/cdialogimpl-class.md)相反。  
  
 消息和事件处理程序可以添加到对话框类中，从类视图。 有关详细信息，请参阅[添加 ATL 消息处理程序](../atl/adding-an-atl-message-handler.md)。  
  
## <a name="adding-a-dialog-box-manually"></a>手动添加一个对话框  
 实现一个对话框是类似于实现一个窗口。 从派生一个类[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)， [CDialogImpl](../atl/reference/cdialogimpl-class.md)，或[CSimpleDialog](../atl/reference/csimpledialog-class.md)和声明[消息映射](../atl/message-maps-atl.md)处理消息。 但是，还必须指定在派生类中的对话框模板资源 ID。 你的类必须具有一个名为的数据成员`IDD`保留此值。  
  
> [!NOTE]
>  当你创建使用 ATL 对话框向导对话框中时，向导会自动添加`IDD`作为成员`enum`类型。  
  
 `CDialogImpl`可实现在安装结束时或承载 Windows 控件的无模式对话框。 `CAxDialogImpl`可实现在安装结束时或承载 ActiveX 和 Windows 控件的无模式对话框。  
  
 若要创建模式对话框，创建的实例你`CDialogImpl`-派生 (或`CAxDialogImpl`-派生) 类，然后调用[DoModal](../atl/reference/cdialogimpl-class.md#domodal)方法。 若要关闭模式对话框，调用[EndDialog](../atl/reference/cdialogimpl-class.md#enddialog)从消息处理程序方法。 若要创建无模式对话框，请调用[创建](../atl/reference/cdialogimpl-class.md#create)方法而不是`DoModal`。 若要销毁无模式对话框中，调用[DestroyWindow](../atl/reference/cdialogimpl-class.md#destroywindow)。  
  
 接收事件将自动完成[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)。 实现对话框的消息处理程序中的处理程序像`CWindowImpl`-派生类。 如果没有特定于消息的返回值，则返回其作为`LRESULT`。 返回`LRESULT`值通过 ATL 映射的 Windows 对话框管理器正确处理。 有关详细信息，请参阅的源代码[CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) atlwin.h 中。  
  
## <a name="example"></a>示例  
 下面的类实现对话框中：  
  
 [!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]  
  
## <a name="see-also"></a>请参阅  
 [窗口类](../atl/atl-window-classes.md)

