---
title: "CMFCRibbonGalleryMenuButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonGalleryMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonGalleryMenuButton class"
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMFCRibbonGalleryMenuButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现包含功能区库的功能区菜单按钮。  
  
## 语法  
  
```  
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](../Topic/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton.md)|构造并初始化一个 `CMFCRibbonGalleryMenuButton` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonGalleryMenuButton::CopyFrom](../Topic/CMFCRibbonGalleryMenuButton::CopyFrom.md)|（重写 [CMFCToolBarMenuButton::CopyFrom](../Topic/CMFCToolBarMenuButton::CopyFrom.md)。）|  
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](../Topic/CMFCRibbonGalleryMenuButton::CreatePopupMenu.md)|（重写 [CMFCToolBarMenuButton::CreatePopupMenu](../Topic/CMFCToolBarMenuButton::CreatePopupMenu.md)。）|  
|[CMFCRibbonGalleryMenuButton::GetPalette](../Topic/CMFCRibbonGalleryMenuButton::GetPalette.md)||  
|[CMFCRibbonGalleryMenuButton::HasButton](../Topic/CMFCRibbonGalleryMenuButton::HasButton.md)|（重写 `CMFCToolBarMenuButton::HasButton`。）|  
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](../Topic/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed.md)|（重写 [CMFCToolBarMenuButton::IsEmptyMenuAllowed](../Topic/CMFCToolBarMenuButton::IsEmptyMenuAllowed.md)。）|  
  
### 备注  
 库菜单按钮显示为带箭头的弹出菜单。  用户单击此按钮时，会显示图像库。  构造库菜单按钮时，必须指定包含这些图像的图像列表。  
  
## 示例  
 下面的示例演示如何采用菜单按钮显示项目符号库：  
  
```  
BOOL CMainFrame::OnShowPopupMenu (CMFCPopupMenu* pMenuPopup)  
{  
    int nBulletIndex = pMenuBar->CommandToIndex (ID_PARA_BULLETS);  
    if (nBulletIndex >= 0)  
    {  
        CMFCToolBarButton* pExButton =  
            pMenuBar->GetButton(nBulletIndex);  
        ASSERT_VALID (pExButton);  
        CMFCRibbonGalleryMenuButton paletteBullet (  
            pExButton->m_nID,  
            pExButton->GetImage (),  
            pExButton->m_strText);  
        InitBulletPalette (&paletteBullet.GetPalette ());  
        pMenuBar->ReplaceButton (ID_PARA_BULLETS, paletteBullet);  
    }  
}  
```  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)  
  
## 要求  
 **标头：**afxRibbonPaletteGallery.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [CMFCRibbonGallery Class](../../mfc/reference/cmfcribbongallery-class.md)