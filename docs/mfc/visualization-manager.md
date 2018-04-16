---
title: "可视化管理器 |Microsoft 文档"
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
- Visualization Manager
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 654ffc0f3fb4c33f153f3389442486ffa86b74a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="visualization-manager"></a>可视化管理器
可视化管理器是控制整个应用程序的外观的对象。 它充当一个类可以放置所有绘图代码应用程序。 MFC 库包含多个视觉管理器。 如果你想要创建你的应用程序的自定义视图，你还可以创建你自己的视觉管理器。 下图显示相同的应用程序时启用不同的视觉管理器：  
  
 ![由 CMFCVisualManagerWindows 呈现的 MyApp](../mfc/media/vmwindows.png "vmwindows")  
使用 CMFCVisualManagerWindows 视觉管理器的 MyApp  
  
 ![由 CMFCVisualManagerVS2005 呈现的 MyApp](../mfc/media/vmvs2005.png "vmvs2005")  
使用 CMFCVisualManagerVS2005 视觉管理器的 MyApp  
  
 ![由 CMFCVisualManagerOfficeXP 呈现的 MyApp](../mfc/media/vmofficexp.png "vmofficexp")  
使用 CMFCVisualManagerOfficeXP 视觉管理器的 MyApp  
  
 ![由 CMFCVisualManagerOffice2003 呈现的 MyApp](../mfc/media/vmoffice2003.png "vmoffice2003")  
使用 CMFCVisualManagerOffice2003 视觉管理器的 MyApp  
  
 ![由 CMFCVisualManagerOffice2007 呈现的 MyApp](../mfc/media/msoffice2007.png "msoffice2007")  
使用 CMFCVisualManagerOffice2007 视觉管理器的 MyApp  
  
 默认情况下，视觉管理器保持几个 GUI 元素的绘制代码。 若要提供自定义 UI 元素，你需要重写视觉管理器的相关绘图方法。 这些方法的列表，请参阅[CMFCVisualManager 类](../mfc/reference/cmfcvisualmanager-class.md)。 可以重写以提供自定义外观的方法是开头的所有方法`OnDraw`。  
  
 你的应用程序只能有一个`CMFCVisualManager`对象。 若要获取指向你的应用程序的可视管理器的指针，请调用静态函数[CMFCVisualManager::GetInstance](../mfc/reference/cmfcvisualmanager-class.md#getinstance)。 因为所有视觉管理器继承自`CMFCVisualManager`、`CMFCVisualManager::GetInstance`方法将获取一个指向适当的视觉管理器，即使创建自定义视觉管理器。  
  
 如果你想要创建自定义视觉管理器，必须先将它派生自视觉管理器已存在。 要派生自的默认类别是`CMFCVisualManager`。 但是，你可以使用不同视觉管理器，如果它更好地类似于是你希望你的应用程序。 例如，如果你想要使用`CMFCVisualManagerOffice2007`视觉管理器，但想仅要更改分隔符的外观、 无法派生从您自定义类`CMFCVisualManagerOffice2007`。 在此方案中，你应覆盖只有绘制分隔符的方法。  
  
 有两种可能的方法要用于你的应用程序特定的视觉管理器。 一种方法是调用[CMFCVisualManager::SetDefaultManager](../mfc/reference/cmfcvisualmanager-class.md#setdefaultmanager)方法并传入作为参数的相应 visual 管理器。 下面的代码示例演示如何将使用`CMFCVisualManagerVS2005`视觉管理器使用此方法：  
  
```  
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));
```  
  
 在你的应用程序中使用视觉管理器的其他方法是手动创建。 在所有呈现，应用程序随后将使用此新的视觉管理器。 但是，因为可能只有一个`CMFCVisualManager`每个应用程序，必须先删除当前视觉管理器，然后创建一个新的对象。 在下面的示例中，`CMyVisualManager`是派生自的自定义可视管理器`CMFCVisualManager`。 以下方法将更改哪些视觉管理器用来显示你的应用程序，具体取决于索引：  
  
```  
void CMyApp::SetSkin (int index)  
{  
    if (CMFCVisualManager::GetInstance() != NULL)  
 {  
    delete CMFCVisualManager::GetInstance();

 }  
 
    switch (index)  
 {  
    case DEFAULT_STYLE: *// The following statement creates a new CMFCVisualManager  
    CMFCVisualManager::GetInstance();
break;  
 
    case CUSTOM_STYLE:  
    new CMyVisualManager;  
    break; 
 
    default: 
    CMFCVisualManager::GetInstance();
break;  
 }  
 
    CMFCVisualManager::GetInstance()->RedrawAll();

} 
```  
  
## <a name="see-also"></a>请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)   
 [CMFCVisualManager 类](../mfc/reference/cmfcvisualmanager-class.md)
