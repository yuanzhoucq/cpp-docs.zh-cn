---
title: 从 ActiveX 控件添加类 (Visual C++) | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322401"
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>从 ActiveX 控件添加类 (Visual C++)
使用此向导从可用的 ActiveX 控件中的接口创建 MFC 类。 可以将 MFC 类添加到 [MFC 应用程序](../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)。  
  
> [!NOTE]
>  无需在启用自动化的情况下创建 MFC 项目，即可从 ActiveX 控件中添加类。  
  
 ActiveX 控件是基于组件对象模型 (COM) 的可重用软件组件，支持各种 OLE 功能，并且可以进行自定义来满足多种软件所需。 在普通的 ActiveX 控件容器中和万维网页面中的 Internet 上均可使用 ActiveX 控件。  
  
### <a name="to-add-an-mfc-class-from-an-activex-control"></a>从 ActiveX 控件添加 MFC 类  
  
1.  在“解决方案资源管理器”或“[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)”中，右键单击要向其添加 ActiveX 控件类的项目的名称。  
  
2.  从快捷菜单中，单击“添加”，然后单击“添加类”。  
  
3.  在“[添加类](../ide/add-class-dialog-box.md)”对话框的“模板”窗格中，单击“ActiveX 控件中的 MFC 类”，然后单击“打开”显示“[从 ActiveX 控件向导添加类](../ide/add-class-from-activex-control-wizard.md)”。  
  
 在向导中，可以在 ActiveX 控件中添加多个接口。 同样，还可以在单个向导会话中从多个 ActiveX 控件创建类。  
  
 可以从已在系统中注册的 ActiveX 控件添加类，也可以从位于类型库文件（.tlb、.olb、.dll、.ocx 或 .exe）中的 ActiveX 控件添加类，无需提前在系统中注册。 请参阅[注册 OLE 控件](../mfc/reference/registering-ole-controls.md)，获取有关注册 ActiveX 控件的详细信息。  
  
 该向导为从所选 ActiveX 控件添加的每个接口创建 MFC 类，该类派生自 [CWnd](../mfc/reference/cwnd-class.md) 或 [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [COM 和 ATL 介绍](../atl/introduction-to-com-and-atl.md)