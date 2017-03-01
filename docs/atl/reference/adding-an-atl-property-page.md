---
title: "ATL 属性页中添加 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: 7b6a6220a33890d99e6fb2bd81ce832b38720c50
ms.lasthandoff: 02/24/2017

---
# <a name="adding-an-atl-property-page"></a>添加 ATL 属性页
若要添加到你的项目的活动模板库 (ATL) 属性页，项目必须已创建作为 ATL 应用程序或包含 ATL 支持的 MFC 应用程序。 您可以使用[ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序或[MFC 应用程序中添加的 ATL 对象](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现对 MFC 应用程序的 ATL 支持。  
  
 如果在添加一个控件的属性页，您的控件必须支持[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)接口。 默认情况下，此接口是在您的控件列表中派生类时您[创建 ATL 控件](../../atl/reference/adding-an-atl-control.md)使用[ATL 控件向导](../../atl/reference/atl-control-wizard.md)。  
  
> [!NOTE]
>  如果您的控件类没有[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)在其派生列表中，您必须手动添加它。  
  
### <a name="to-add-an-atl-property-page-to-your-project"></a>若要向项目添加 ATL 属性页  
  
1.  在上述**解决方案资源管理器**或[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，右键单击您想要添加的 ATL 属性页的项目的名称。  
  
2.  从快捷菜单中，单击**添加**，然后单击**添加类**。  
  
3.  在[添加类](../../ide/add-class-dialog-box.md)对话框中，在模板窗格中，单击**ATL 属性页**，然后单击**打开**显示[ATL 属性页向导](../../atl/reference/atl-property-page-wizard.md)。  
  
 一旦您创建控件的属性页，您必须提供[PROP_PAGE](http://msdn.microsoft.com/library/2155973e-b96c-4385-bf85-5d6112c969b8)中控件的属性映射条目。  
  
## <a name="see-also"></a>另请参阅  
 [属性页](../../atl/atl-com-property-pages.md)   
 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)   
 [示例︰ 实现属性页](../../atl/example-implementing-a-property-page.md)


