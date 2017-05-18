---
title: "添加 ATL 属性页 |Microsoft 文档"
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 72a8644d81857b722fd50a7e852d215bb25a2fb2
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="adding-an-atl-property-page"></a>添加 ATL 属性页
若要将活动模板库 (ATL) 属性页添加到你的项目，你的项目必须已创建作为 ATL 应用程序或 MFC 应用程序包含 ATL 支持。 你可以使用[ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序或[ATL 对象添加到 MFC 应用程序](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)实现为 MFC 应用程序的 ATL 支持。  
  
 如果要添加的控件属性页，控件必须支持[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)接口。 默认情况下，此接口是在派生列表控件的类时你[创建 ATL 控件](../../atl/reference/adding-an-atl-control.md)使用[ATL 控件向导](../../atl/reference/atl-control-wizard.md)。  
  
> [!NOTE]
>  如果你的控件类没有[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)在其派生列表中，你必须手动添加它。  
  
### <a name="to-add-an-atl-property-page-to-your-project"></a>若要向项目添加 ATL 属性页  
  
1.  在**解决方案资源管理器**或[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，右键单击你想要添加的 ATL 属性页项目的名称。  
  
2.  从快捷菜单中，单击**添加**，然后单击**添加类**。  
  
3.  在[添加类](../../ide/add-class-dialog-box.md)对话框中，在模板窗格中，单击**ATL 属性页**，然后单击**打开**以显示[ATL 属性页向导](../../atl/reference/atl-property-page-wizard.md)。  
  
 一旦你创建的控件属性页，你必须提供[PROP_PAGE](property-map-macros.md#prop_page)中控件的属性映射条目。  
  
## <a name="see-also"></a>另请参阅  
 [属性页](../../atl/atl-com-property-pages.md)   
 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)   
 [示例：实现属性页](../../atl/example-implementing-a-property-page.md)


