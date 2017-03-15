---
title: "Implementing a Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 对话框"
  - "CAxDialogImpl class, implementing dialog boxes in ATL"
  - "CSimpleDialog class, implementing dialog boxes in ATL"
  - "对话框, ATL"
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Implementing a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有两种方式将对话框添加到您的ATL项目:使用ATL对话框向导"或手动添加。  
  
## 将ATL对话框向导的对话框  
 在 [添加选件类对话框](../ide/add-class-dialog-box.md)，选择ATL对话框对象添加对话框向ATL项目。  填充ATL对话框向导"为合适然后单击 **Finish**。  该向导将从 [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) 派生的选件类添加到项目中。  从打开 **视图** 菜单上的"资源视图"中，找到您的对话框，并双击以打开它在资源编辑器。  
  
> [!NOTE]
>  如果对话框从 `CAxDialogImpl`派生，它可以承载ActiveX和Windows控件。  如果不需要开销ActiveX控件支持在对话框选件类，使用 [CSimpleDialog](../atl/reference/csimpledialog-class.md) 或 [CDialogImpl](../atl/reference/cdialogimpl-class.md)。  
  
 消息和事件处理程序可以添加到您的对话框选件类从选件类视图。  有关更多信息，请参见[添加 ATL 消息处理程序](../atl/adding-an-atl-message-handler.md)。  
  
## 手动添加对话框  
 实现对话框类似于实现窗口。  您从 [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)、 [CDialogImpl](../atl/reference/cdialogimpl-class.md)或 [CSimpleDialog](../atl/reference/csimpledialog-class.md) 派生选件类并声明 [消息映射](../atl/message-maps-atl.md) 处理消息。  但是，您在派生类还必须指定对话框模板资源ID。  您的选件类必须具有数据成员调用表示该值的 `IDD`。  
  
> [!NOTE]
>  使用ATL对话框向导"时，将创建一个对话框，向导会自动添加 `IDD` 成员作为 `enum` 类型。  
  
 `CDialogImpl` 可以实现该模式或无模式对话框宿主Windows控件。  `CAxDialogImpl` 可以实现承载ActiveX和Windows控件的模式或无模式对话框。  
  
 若要创建一个模式对话框，请创建您的 `CDialogImpl`实例派生的\(或 `CAxDialogImpl`派生\)选件类随后调用 [DoModal](../Topic/CDialogImpl::DoModal.md) 方法。  若要关闭有模式对话框，请从消息处理程序的 [EndDialog](../Topic/CDialogImpl::EndDialog.md) 方法。  若要创建无模式对话框，请调用 [创建](../Topic/CDialogImpl::Create.md) 方法而不是 `DoModal`。  若要销毁无模式对话框，请调用 [DestroyWindow](../Topic/CDialogImpl::DestroyWindow.md)。  
  
 接收事件在 [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)自动执行。  实现对话框的消息处理程序中，您将 `CWindowImpl`的处理程序的派生类。  如果使用消息特定的返回值，则返回为 `LRESULT`。  返回的 `LRESULT` 值由适当地处理的ATL映射由Windows对话框管理器。  有关详细信息，请在atlwin.h的 [CDialogImplBaseT::DialogProc](../Topic/CDialogImpl::DialogProc.md) 请参见源代码。  
  
## 示例  
 下面选件类实现一个对话框:  
  
 [!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/CPP/implementing-a-dialog-box_1.h)]  
  
## 请参阅  
 [窗口类](../atl/atl-window-classes.md)