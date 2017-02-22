---
title: "CMFCVisualManagerWindows7 Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxvisualmanagerwindows7/CMFCVisualManagerWindows7"
  - "CMFCVisualManagerWindows7"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerWindows7 class"
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CMFCVisualManagerWindows7 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCVisualManagerWindows7` 为应用程序 [!INCLUDE[win7](../../build/includes/win7_md.md)] 应用程序的外观。  
  
## 语法  
  
```  
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCVisualManagerWindows7::CMFCVisualManagerWindows7](../Topic/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7.md)|默认构造函数。|  
|[CMFCVisualManagerWindows7::~CMFCVisualManagerWindows7](../Topic/CMFCVisualManagerWindows7::~CMFCVisualManagerWindows7.md)|默认析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCVisualManagerWindows7::CleanStyle`|清除当前视觉样式并重置默认视觉样式。|  
|`CMFCVisualManagerWindows7::CleanUp`|清除所有在用户界面中的对象并重置菜单。|  
|`CMFCVisualManagerWindows7::DrawNcBtn`|在非工作区绘制一个按钮）。  框架使用此方法绘制，最小化、最大化，关闭并还原按钮在窗架的右上角。  当程序使用非Aero主题时，不会调用此方法。|  
|`CMFCVisualManagerWindows7::DrawNcText`|在非工作区绘制文本在框架。  框架在标题栏使用此方法绘制应用程序标题在框架窗口的顶部。|  
|`CMFCVisualManagerWindows7::DrawSeparator`|绘制在 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)的分隔符。|  
|`CMFCVisualManagerWindows7::GetRibbonBar`|检索 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md) 与用户界面。|  
|[CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor](../Topic/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor.md)|获取功能区编辑框背景色。|  
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|重写 [CMFCVisualManager::GetRibbonPopupBorderSize](../Topic/CMFCVisualManager::GetRibbonPopupBorderSize.md)|  
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|重写 [CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset](../Topic/CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset.md)|  
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|重写 [CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin](../Topic/CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin.md)|  
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|重写 [CMFCVisualManagerWindows::IsHighlightWholeMenuItem](../Topic/CMFCVisualManagerWindows::IsHighlightWholeMenuItem.md)|  
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|重写 [CMFCVisualManager::IsOwnerDrawMenuCheck](../Topic/CMFCVisualManager::IsOwnerDrawMenuCheck.md)|  
|`CMFCVisualManagerWindows7::IsRibbonPresent`|确定 `CMFCRibbonBar` 是否存在且变为可见的。|  
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|重写 [CMFCVisualManagerWindows::OnDrawButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawButtonBorder.md)|  
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|重写 [CMFCVisualManagerWindows::OnDrawCheckBoxEx](../Topic/CMFCVisualManagerWindows::OnDrawCheckBoxEx.md)|  
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|重写 [CMFCVisualManagerWindows::OnDrawComboDropButton](../Topic/CMFCVisualManagerWindows::OnDrawComboDropButton.md)|  
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|重写 [CMFCVisualManager::OnDrawDefaultRibbonImage](../Topic/CMFCVisualManager::OnDrawDefaultRibbonImage.md)|  
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|重写 [CMFCVisualManagerWindows::OnDrawMenuBorder](../Topic/CMFCVisualManagerWindows::OnDrawMenuBorder.md)|  
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|重写 [CMFCVisualManager::OnDrawMenuCheck](../Topic/CMFCVisualManager::OnDrawMenuCheck.md)|  
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|重写 [CMFCVisualManager::OnDrawMenuLabel](../Topic/CMFCVisualManager::OnDrawMenuLabel.md)|  
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|重写 `CMFCVisualManager::OnDrawRadioButton`|  
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|重写 [CMFCVisualManager::OnDrawRibbonApplicationButton](../Topic/CMFCVisualManager::OnDrawRibbonApplicationButton.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|重写 [CMFCVisualManager::OnDrawRibbonButtonBorder](../Topic/CMFCVisualManager::OnDrawRibbonButtonBorder.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|重写 [CMFCVisualManager::OnDrawRibbonCaption](../Topic/CMFCVisualManager::OnDrawRibbonCaption.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|重写 [CMFCVisualManager::OnDrawRibbonCaptionButton](../Topic/CMFCVisualManager::OnDrawRibbonCaptionButton.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|重写 [CMFCVisualManager::OnDrawRibbonCategory](../Topic/CMFCVisualManager::OnDrawRibbonCategory.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|重写 [CMFCVisualManager::OnDrawRibbonCategoryTab](../Topic/CMFCVisualManager::OnDrawRibbonCategoryTab.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|重写 [CMFCVisualManager::OnDrawRibbonDefaultPaneButton](../Topic/CMFCVisualManager::OnDrawRibbonDefaultPaneButton.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|重写 [CMFCVisualManager::OnDrawRibbonGalleryButton](../Topic/CMFCVisualManager::OnDrawRibbonGalleryButton.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|重写 `CMFCVisualManager::OnDrawRibbonLaunchButton`|  
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|重写 [CMFCVisualManager::OnDrawRibbonMenuCheckFrame](../Topic/CMFCVisualManager::OnDrawRibbonMenuCheckFrame.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|重写 [CMFCVisualManager::OnDrawRibbonPanel](../Topic/CMFCVisualManager::OnDrawRibbonPanel.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|重写 [CMFCVisualManager::OnDrawRibbonPanelCaption](../Topic/CMFCVisualManager::OnDrawRibbonPanelCaption.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|重写 [CMFCVisualManager::OnDrawRibbonProgressBar](../Topic/CMFCVisualManager::OnDrawRibbonProgressBar.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|重写 [CMFCVisualManager::OnDrawRibbonRecentFilesFrame](../Topic/CMFCVisualManager::OnDrawRibbonRecentFilesFrame.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|重写 [CMFCVisualManager::OnDrawRibbonSliderChannel](../Topic/CMFCVisualManager::OnDrawRibbonSliderChannel.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|重写 [CMFCVisualManager::OnDrawRibbonSliderThumb](../Topic/CMFCVisualManager::OnDrawRibbonSliderThumb.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|重写 [CMFCVisualManager::OnDrawRibbonSliderZoomButton](../Topic/CMFCVisualManager::OnDrawRibbonSliderZoomButton.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|重写 [CMFCVisualManager::OnDrawRibbonStatusBarPane](../Topic/CMFCVisualManager::OnDrawRibbonStatusBarPane.md)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|重写 [CMFCVisualManager::OnDrawRibbonTabsFrame](../Topic/CMFCVisualManager::OnDrawRibbonTabsFrame.md)|  
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|重写 [CMFCVisualManagerWindows::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarSizeBox.md)|  
|`CMFCVisualManagerWindows7::OnFillBarBackground`|重写 [CMFCVisualManagerWindows::OnFillBarBackground](../Topic/CMFCVisualManagerWindows::OnFillBarBackground.md)|  
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|重写 [CMFCVisualManagerWindows::OnFillButtonInterior](../Topic/CMFCVisualManagerWindows::OnFillButtonInterior.md)|  
|[CMFCVisualManagerWindows7::OnFillMenuImageRect](../Topic/CMFCVisualManagerWindows7::OnFillMenuImageRect.md)|在菜单项的图像周围时，加载区框架调用此方法。|  
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|重写 [CMFCVisualManager::OnFillRibbonButton](../Topic/CMFCVisualManager::OnFillRibbonButton.md)|  
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|重写 [CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup](../Topic/CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup.md)|  
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|重写 [CMFCVisualManagerWindows::OnHighlightMenuItem](../Topic/CMFCVisualManagerWindows::OnHighlightMenuItem.md)|  
|`CMFCVisualManagerWindows7::OnNcActivate`|重写 [CMFCVisualManager::OnNcActivate](../Topic/CMFCVisualManager::OnNcActivate.md)|  
|`CMFCVisualManagerWindows7::OnNcPaint`|重写 [CMFCVisualManager::OnNcPaint](../Topic/CMFCVisualManager::OnNcPaint.md)|  
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|重写 [CMFCVisualManagerWindows::OnUpdateSystemColors](../Topic/CMFCVisualManagerWindows::OnUpdateSystemColors.md)|  
|`CMFCVisualManagerWindows7::SetResourceHandle`|设置描述视觉管理器的属性的资源句柄。|  
|`CMFCVisualManagerWindows7::SetStyle`|设置 `CMFCVisualManagerWindows7` GUI的配色方案。|  
  
## 备注  
 使用 `CMFCVisualManagerWindows7` 选件类来更改应用程序的外观模式默认 [!INCLUDE[win7](../../build/includes/win7_md.md)] 应用程序。  如果应用程序在Windows的版本早于 [!INCLUDE[win7](../../build/includes/win7_md.md)]，运行此选件类可能不是有效的。  在这种情况下，使用默认视觉管理器中定义的应用程序在 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)。  
  
 CMFCVisualManagerWindows7继承 [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md) 和 `CMFCVisualManager` 选件类的多个方法。  上一节中列出的方法是方法的新功能 `CMFCVisualManagerWindows7` 选件类。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)  
  
 `CMFCVisualManagerWindows7`  
  
## 要求  
 **标头:** afxvisualmanagerwindows7.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)