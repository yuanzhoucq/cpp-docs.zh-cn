---
title: "可视化管理器 | Microsoft Docs"
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
  - "可视化管理器"
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 可视化管理器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

视觉管理器是对象控件的整个应用程序的外观。  是可将应用程序中的任何绘图代码的单个类。  MFC 库包括几视觉管理器。  如果要创建自定义视图应用程序，您也可以创建自己视觉管理器。  当不同的视觉管理器启用时，下面的图像演示同一应用程序：  
  
 ![由 CMFCVisualManagerWindows 呈现的 MyApp](../Image/VMWindows.png "VMWindows")  
使用 CMFCVisualManagerWindows 视觉管理器中名为 MyApp  
  
 ![由 CMFCVisualManagerVS2005 呈现的 MyApp](../mfc/media/vmvs2005.png "VMVS2005")  
使用 CMFCVisualManagerVS2005 视觉管理器中名为 MyApp  
  
 ![由 CMFCVisualManagerOfficeXP 呈现的 MyApp](../mfc/media/vmofficexp.png "VMOfficeXP")  
使用 CMFCVisualManagerOfficeXP 视觉管理器中名为 MyApp  
  
 ![由 CMFCVisualManagerOffice2003 呈现的 MyApp](../mfc/media/vmoffice2003.png "VMOffice2003")  
使用 CMFCVisualManagerOffice2003 视觉管理器中名为 MyApp  
  
 ![由 CMFCVisualManagerOffice2007 呈现的 MyApp](../mfc/media/msoffice2007.png "MSOffice2007")  
使用 CMFCVisualManagerOffice2007 视觉管理器中名为 MyApp  
  
 默认情况下，虚拟管理器会维护几 GUI 元素的绘图代码。  若要提供自定义 UI 元素，您需要重写虚拟管理器相关的绘制方法。  有关这些方法列表，请参见 [CMFCVisualManager Class](../mfc/reference/cmfcvisualmanager-class.md)。  可以重写的自定义外观的方法是以 `OnDraw`的所有方法。  
  
 应用程序只能有一个 `CMFCVisualManager` 对象。  要获取指向应用程序的视觉管理器，请调用静态函数 [CMFCVisualManager::GetInstance](../Topic/CMFCVisualManager::GetInstance.md)。  由于所有虚拟管理器从 `CMFCVisualManager`继承，则 `CMFCVisualManager::GetInstance` 方法将一个指向相应的虚拟管理器，即使创建自定义虚拟管理器。  
  
 如果您希望创建自定义虚拟管理器，则必须从现有的虚拟管理器派生。  默认 `CMFCVisualManager`是从派生的类。  但是，您可以使用不同的视觉管理器，则更好类似于您的应用程序需要。  例如，在中，如果要使用 `CMFCVisualManagerOffice2007` 虚管理器，但是，若要只更改分隔符如何查找，可以从 `CMFCVisualManagerOffice2007`派生自定义类。  在这种情况下，您应覆盖绘制的分隔符只有方法。  
  
 有两种可能的情况下用作应用程序特定虚拟管理器。  一种方法是调用 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md) 方法并传入相应的虚拟管理器作为参数。  下面的代码示例演示如何将对该方法的虚拟 `CMFCVisualManagerVS2005` 管理器：  
  
```  
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));  
```  
  
 另一个方式使用视觉管理器在应用程序中手动创建它。  应用程序的所有呈现将使用了这一新的视觉管理器。  但是，因为，应用程序只能有每一个 `CMFCVisualManager` 对象，您必须删除当前视觉管理器中，创建新的。  在下面的示例中，`CMyVisualManager` 是 `CMFCVisualManager`派生的自定义虚拟管理器。  以下方法根据索引将更改的视觉管理器用于查看应用程序，例如：  
  
```  
void CMyApp::SetSkin (int index)  
{  
   if (CMFCVisualManager::GetInstance() != NULL)  
   {  
      delete CMFCVisualManager::GetInstance();  
   }  
  
   switch (index)  
   {  
   case DEFAULT_STYLE:  
      // The following statement creates a new CMFCVisualManager  
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
  
## 请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)   
 [CMFCVisualManager Class](../mfc/reference/cmfcvisualmanager-class.md)