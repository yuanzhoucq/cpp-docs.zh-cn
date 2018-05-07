---
title: 从 ActiveX 控件 （Visual c + +） 添加类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 793adf38da33808371a0df71f671c3e29da75326
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>从 ActiveX 控件添加类 (Visual C++)
使用此向导创建 MFC 类时从中可用的 ActiveX 控件的接口。 你可以添加到的 MFC 类[MFC 应用程序](../mfc/reference/creating-an-mfc-application.md)、 [MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md)，或[MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)。  
  
> [!NOTE]
>  不需要使用启用 ActiveX 控件中添加类的自动化创建 MFC 项目。  
  
 ActiveX 控件是基于组件对象模型 (COM) 支持各种各样的 OLE 功能，可以自定义以满足许多软件需求的可重用软件组件。 ActiveX 控件被设计用于在普通的 ActiveX 控件容器和全球通用的网页中 Internet 上。  
  
### <a name="to-add-an-mfc-class-from-an-activex-control"></a>若要从 ActiveX 控件添加的 MFC 类  
  
1.  在**解决方案资源管理器**或[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，右键单击你想要添加的 ActiveX 控件类的项目的名称。  
  
2.  从快捷菜单中，单击**添加**，然后单击**添加类**。  
  
3.  在[添加类](../ide/add-class-dialog-box.md)对话框中，在模板窗格中，单击**ActiveX 控件中的 MFC 类**，然后单击**打开**以显示[从 ActiveX 中添加类向导的控件](../ide/add-class-from-activex-control-wizard.md)。  
  
 在向导中，你可以添加多个接口的 ActiveX 控件中。 同样，你可以创建类从多个 ActiveX 控件在单个向导会话中。  
  
 你可以从在你的系统中注册的 ActiveX 控件添加类，也可以从位于类型库文件 （.tlb、.olb、.dll、.ocx 或.exe），注册的情况下第一个系统中的 ActiveX 控件添加类。 请参阅[注册 OLE 控件](../mfc/reference/registering-ole-controls.md)有关注册 ActiveX 控件的详细信息。  
  
 该向导创建的 MFC 类，派生自[CWnd](../mfc/reference/cwnd-class.md)或从[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)，为你从所选的 ActiveX 控件添加每个接口。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [COM 和 ATL 介绍](../atl/introduction-to-com-and-atl.md)