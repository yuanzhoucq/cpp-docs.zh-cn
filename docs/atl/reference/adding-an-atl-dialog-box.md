---
title: "添加 ATL 对话框中 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d8c9969f4747c6c3fa2a39b7b0452f6ac54c9d58
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-atl-dialog-box"></a>添加一个 ATL 对话框
要向你的项目添加 ATL 对话框，你的项目必须包括 ATL 支持的 MFC 项目或者 ATL 项目中。 你可以使用[ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或[ATL 对象添加到 MFC 应用程序](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)实现为 MFC 应用程序的 ATL 支持。  
  
 默认情况下，ATL 对话框向导实现派生自一个对话框[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)。 此类包括支持托管 ActiveX 和 Windows 控件。 如果向导已生成你的代码后，你不会希望 ActiveX 控件支持的开销的所有实例都替换`CAxDialogImpl`使用[CSimpleDialog](../../atl/reference/csimpledialog-class.md)或[CDialogImpl](../../atl/reference/cdialogimpl-class.md)作为基类.  
  
> [!NOTE]
>  `CSimpleDialog`创建仅支持 Windows 公共控件的模式对话框框。 `CDialogImpl`创建任一模式或无模式对话框。  
  
### <a name="to-add-an-atl-dialog-resource-to-your-project"></a>若要向项目添加 ATL 对话框资源  
  
1.  ATL 项目使用创建[ATL 项目向导](../../atl/reference/atl-project-wizard.md)。  
  
2.  从[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，右键单击项目名称，然后单击**添加**从快捷菜单。 单击**添加类**。  
  
3.  在模板窗格中的[添加类](../../ide/add-class-dialog-box.md)对话框中，单击**ATL 对话框**。 单击**打开**以显示[ATL 对话框向导](../../atl/reference/atl-dialog-wizard.md)。  
  
 有关详细信息，请参阅[实现对话框](../../atl/implementing-a-dialog-box.md)。  
  
## <a name="see-also"></a>请参阅  
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [窗口类](../../atl/atl-window-classes.md)   
 [消息映射](../../atl/message-maps-atl.md)

