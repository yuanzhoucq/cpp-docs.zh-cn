---
title: "CMFCRibbonGalleryMenuButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CopyFrom
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CreatePopupMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::GetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::HasButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonGalleryMenuButton class
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: dce01ac22db0ff28e8f07b6d30f6418a61ad68d5
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbongallerymenubutton-class"></a>CMFCRibbonGalleryMenuButton 类
实现包含功能区库的功能区菜单按钮。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](#cmfcribbongallerymenubutton)|构造并初始化一个 `CMFCRibbonGalleryMenuButton` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonGalleryMenuButton::CopyFrom](#copyfrom)|(重写[CMFCToolBarMenuButton::CopyFrom](../../mfc/reference/cmfctoolbarmenubutton-class.md#copyfrom)。)|  
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](#createpopupmenu)|(重写[CMFCToolBarMenuButton::CreatePopupMenu](../../mfc/reference/cmfctoolbarmenubutton-class.md#createpopupmenu)。)|  
|[CMFCRibbonGalleryMenuButton::GetPalette](#getpalette)||  
|[CMFCRibbonGalleryMenuButton::HasButton](#hasbutton)|（重写 `CMFCToolBarMenuButton::HasButton`。）|  
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|(重写[CMFCToolBarMenuButton::IsEmptyMenuAllowed](../../mfc/reference/cmfctoolbarmenubutton-class.md#isemptymenuallowed)。)|  
  
### <a name="remarks"></a>备注  
 库菜单按钮显示为带箭头的弹出菜单。 用户单击此按钮时，会显示图像库。 构造库菜单按钮时，必须指定包含这些图像的图像列表。  
  
## <a name="example"></a>示例  
 下面的示例演示如何采用菜单按钮显示项目符号库：  
  
```  
BOOL CMainFrame::OnShowPopupMenu (CMFCPopupMenu* pMenuPopup)  
{  
    int nBulletIndex = pMenuBar->CommandToIndex (ID_PARA_BULLETS);

    if (nBulletIndex>= 0)  
 {  
    CMFCToolBarButton* pExButton = 
    pMenuBar->GetButton(nBulletIndex);
ASSERT_VALID (pExButton);

    CMFCRibbonGalleryMenuButton paletteBullet (
    pExButton->m_nID, 
    pExButton->GetImage (),  
    pExButton->m_strText);

 InitBulletPalette (&paletteBullet.GetPalette ());

    pMenuBar->ReplaceButton (ID_PARA_BULLETS,
    paletteBullet);

 }  
}  
```  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxRibbonPaletteGallery.h  
  
##  <a name="copyfrom"></a>CMFCRibbonGalleryMenuButton::CopyFrom  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
  
### <a name="remarks"></a>备注  
  
##  <a name="cmfcribbongallerymenubutton"></a>CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton  
 构造并初始化[CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)对象。  
  
```  
CMFCRibbonGalleryMenuButton(
    UINT uiID,  
    int iImage,  
    LPCTSTR lpszText,  
    CMFCToolBarImages& imagesPalette);

 
CMFCRibbonGalleryMenuButton(
    UINT uiID,  
    int iImage,  
    LPCTSTR lpszText,  
    UINT uiImagesPaletteResID = 0,  
    int cxPaletteImage = 0);
```  
  
### <a name="parameters"></a>参数  
 `uiID`  
 按钮的命令 ID。 这是在中发送的值**WM_COMMAND**消息当用户单击此按钮。  
  
 `iImage`  
 若要使用库菜单按钮显示的图像的索引。 图像存储在`imagesPalette`参数。  
  
 `lpszText`  
 要在菜单按钮上显示的文本。  
  
 `imagesPalette`  
 包含在库中显示的图像的列表。  
  
 `uiImagesPaletteResID`  
 要在库中显示图像的图像列表的资源 ID。  
  
 `cxPaletteImage`  
 指定以像素为单位，要在库中显示的图像的宽度。  
  
### <a name="remarks"></a>备注  
 库菜单按钮显示为带有箭头的弹出菜单。 用户单击此按钮时，会显示图像库。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用的构造函数`CMFCRibbonGalleryMenuButton`类。 此代码段属于[MS Office 2007 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&8;](../../mfc/reference/codesnippet/cpp/cmfcribbongallerymenubutton-class_1.cpp)]  
  
##  <a name="createpopupmenu"></a>CMFCRibbonGalleryMenuButton::CreatePopupMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpalette"></a>CMFCRibbonGalleryMenuButton::GetPalette  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonGallery& GetPalette();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="hasbutton"></a>CMFCRibbonGalleryMenuButton::HasButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasButton() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isemptymenuallowed"></a>CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [CMFCRibbonGallery 类](../../mfc/reference/cmfcribbongallery-class.md)

