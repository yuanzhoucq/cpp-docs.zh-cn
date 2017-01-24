---
title: "Adding an ATL Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, 添加对话框资源"
  - "对话框, ATL"
  - "MFC 对话框, ATL 对话"
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding an ATL Dialog Box
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要将 ATL 对话框添加到项目中，项目必须是 ATL 项目或包含 ATL 支持的 MFC 项目。  可使用 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或者[向 MFC 应用程序项目添加 ATL 对象](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现 MFC 应用程序的 ATL 支持。  
  
 默认情况下，“ATL 对话框向导”实现从 [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md) 导出的对话框。  此类包含对宿主 ActiveX 和 Windows 控件的支持。  如果不想要 ActiveX 控件支持的系统开销，当向导生成代码后，请使用 [CSimpleDialog](../../atl/reference/csimpledialog-class.md) 或 [CDialogImpl](../../atl/reference/cdialogimpl-class.md) 将 `CAxDialogImpl` 的所有实例替换为基类。  
  
> [!NOTE]
>  `CSimpleDialog` 仅创建只支持 Windows 公共控件的模式对话框。  `CDialogImpl` 既创建模式对话框，也创建无模式对话框。  
  
### 将 ATL 对话框资源添加到项目中  
  
1.  使用 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 项目。  
  
2.  从[“类视图”](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中右击项目名称，然后单击快捷菜单上的“添加”。  单击“添加类”。  
  
3.  在[添加类](../../ide/add-class-dialog-box.md)对话框的“模板”窗格中，单击“ATL 对话框”。  单击“打开”以显示 [ATL 对话框向导](../../atl/reference/atl-dialog-wizard.md)。  
  
 有关更多信息，请参见[实现对话框](../../atl/implementing-a-dialog-box.md)。  
  
## 请参阅  
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [窗口类](../../atl/atl-window-classes.md)   
 [Message Maps](../../atl/message-maps-atl.md)