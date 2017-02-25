---
title: "添加 ATL 属性页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, 添加属性页"
  - "控件 [ATL], 属性页"
  - "属性页, 添加"
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 添加 ATL 属性页
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要向项目中添加活动模板库 \(ATL\) 属性页，项目必须已创建为 ATL 应用程序或包含 ATL 支持的 MFC 应用程序。  可使用 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或者[向 MFC 应用程序项目添加 ATL 对象](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现 MFC 应用程序的 ATL 支持。  
  
 如果要为控件添加属性页，控件必须支持 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) 接口。  默认情况下，使用 [ATL 控件向导](../../atl/reference/atl-control-wizard.md)来[创建 ATL 控件](../../atl/reference/adding-an-atl-control.md)时，该接口在控件类的导出列表中。  
  
> [!NOTE]
>  如果控件类的派生列表中没有 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)，则必须手动添加。  
  
### 向项目中添加 ATL 属性页  
  
1.  在**“解决方案资源管理器”**或[类视图](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，右击要添加 ATL 属性页的项目的名称。  
  
2.  从快捷菜单中单击“添加”，然后单击“添加类”。  
  
3.  在[添加类](../../ide/add-class-dialog-box.md)对话框中的“模板”窗格中，单击“ATL 属性页”，然后单击“打开”显示 [ATL 属性页向导](../../atl/reference/atl-property-page-wizard.md)。  
  
 为控件创建了属性页后，必须在属性映射中为控件提供 [PROP\_PAGE](../Topic/PROP_PAGE.md) 项。  
  
## 请参阅  
 [属性页](../../atl/atl-com-property-pages.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [Example: Implementing a Property Page](../../atl/example-implementing-a-property-page.md)