---
title: "从 ActiveX 控件添加类 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 添加类"
  - "类 [C++], 创建"
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 从 ActiveX 控件添加类 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用该向导从可用 ActiveX 控件的接口创建 MFC 类。  可以向 [MFC 应用程序](../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)中添加 MFC 类。  
  
> [!NOTE]
>  不需要创建启用自动化的 MFC 项目，也可以从 ActiveX 控件添加类。  
  
 ActiveX 控件是基于组件对象模型 \(COM\) 的可重用软件组件，它支持广泛的 OLE 功能并可自定义以满足多种软件的需要。  ActiveX 控件旨在用于普通的 ActiveX 控件容器和 Internet 上的万维网页。  
  
### 从 ActiveX 控件添加 MFC 类  
  
1.  在**解决方案资源管理器**或[“类视图”](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，右击要向其中添加 ActiveX 控件类的项目的名称。  
  
2.  从快捷菜单中单击“添加”，然后单击“添加类”。  
  
3.  在[添加类](../ide/add-class-dialog-box.md)对话框的“模板”窗格中，单击“ActiveX 控件中的 MFC 类”，然后单击“打开”以显示[从 ActiveX 控件向导添加类](../ide/add-class-from-activex-control-wizard.md)。  
  
 在该向导中，可以在 ActiveX 控件中添加多个接口。  同样，可以在单个向导会话中从多个 ActiveX 控件创建类。  
  
 可以从系统中注册的 ActiveX 控件添加类，也可从位于类型库文件（.tlb、.olb、.dll、.ocx 或 .exe）中的 ActiveX 控件添加类，而无需先在系统中注册这些控件。  有关注册 ActiveX 控件的更多信息，请参见[注册 OLE 控件](../mfc/reference/registering-ole-controls.md)。  
  
 该向导为从选定的 ActiveX 控件添加的每个接口创建 MFC 类（派生自 [CWnd](../mfc/reference/cwnd-class.md) 或 [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)）。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [Introduction to COM and ATL](../atl/introduction-to-com-and-atl.md)