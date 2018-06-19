---
title: CMFCVisualManagerWindows7 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::OnFillMenuImageRect
dev_langs:
- C++
helpviewer_keywords:
- CMFCVisualManagerWindows7 Class [MFC]
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6599ddf3663f56c651907fe3823849787a05b50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373698"
---
# <a name="cmfcvisualmanagerwindows7-class"></a>CMFCVisualManagerWindows7 类
`CMFCVisualManagerWindows7` ，应用程序的外观[!INCLUDE[win7](../../build/includes/win7_md.md)]应用程序。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCVisualManagerWindows7::CMFCVisualManagerWindows7](#cmfcvisualmanagerwindows7)|默认构造函数。|  
|[CMFCVisualManagerWindows7:: ~ CMFCVisualManagerWindows7](#cmfcvisualmanagerwindows7__~cmfcvisualmanagerwindows7)|在默认析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCVisualManagerWindows7::CleanStyle`|清除当前的视觉样式，并重置默认的视觉样式。|  
|`CMFCVisualManagerWindows7::CleanUp`|清除所有用户界面中的对象，并重置菜单。|  
|`CMFCVisualManagerWindows7::DrawNcBtn`|在帧上的非工作区中绘制一个按钮。 此方法，以便绘制尽量减少，框架将使用最大化，请关闭并还原窗口框架的右上角中的按钮。 该程序使用非 Aero 主题时，不调用此方法。|  
|`CMFCVisualManagerWindows7::DrawNcText`|在帧上的非工作区中绘制文本。 框架使用此方法来绘制在框架窗口顶部的标题栏中的应用程序标题。|  
|`CMFCVisualManagerWindows7::DrawSeparator`|在上绘制分隔符[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)。|  
|`CMFCVisualManagerWindows7::GetRibbonBar`|检索[CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)与用户界面相关联。|  
|[CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor](#getribboneditbackgroundcolor)|获取功能区编辑框背景色。|  
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|重写[CMFCVisualManager::GetRibbonPopupBorderSize](../../mfc/reference/cmfcvisualmanager-class.md#getribbonpopupbordersize)|  
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|重写[CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarchevronoffset)|  
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|重写[CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarrightmargin)|  
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|重写[CMFCVisualManagerWindows::IsHighlightWholeMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ishighlightwholemenuitem)|  
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|重写[CMFCVisualManager::IsOwnerDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#isownerdrawmenucheck)|  
|`CMFCVisualManagerWindows7::IsRibbonPresent`|确定是否`CMFCRibbonBar`是否存在并且可见。|  
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|重写[CMFCVisualManagerWindows::OnDrawButtonBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawbuttonborder)|  
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|重写[CMFCVisualManagerWindows::OnDrawCheckBoxEx](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcheckboxex)|  
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|重写[CMFCVisualManagerWindows::OnDrawComboDropButton](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcombodropbutton)|  
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|重写[CMFCVisualManager::OnDrawDefaultRibbonImage](../../mfc/reference/cmfcvisualmanager-class.md#ondrawdefaultribbonimage)|  
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|重写[CMFCVisualManagerWindows::OnDrawMenuBorder](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawmenuborder)|  
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|重写[CMFCVisualManager::OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck)|  
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|重写[CMFCVisualManager::OnDrawMenuLabel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenulabel)|  
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|重写 `CMFCVisualManager::OnDrawRadioButton`|  
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|重写[CMFCVisualManager::OnDrawRibbonApplicationButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonapplicationbutton)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|重写[CMFCVisualManager::OnDrawRibbonButtonBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonborder)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|重写[CMFCVisualManager::OnDrawRibbonCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaption)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|重写[CMFCVisualManager::OnDrawRibbonCaptionButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaptionbutton)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|重写[CMFCVisualManager::OnDrawRibbonCategory](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategory)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|重写[CMFCVisualManager::OnDrawRibbonCategoryTab](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|重写[CMFCVisualManager::OnDrawRibbonDefaultPaneButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbondefaultpanebutton)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|重写[CMFCVisualManager::OnDrawRibbonGalleryButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbongallerybutton)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|重写 `CMFCVisualManager::OnDrawRibbonLaunchButton`|  
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|重写[CMFCVisualManager::OnDrawRibbonMenuCheckFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonmenucheckframe)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|重写[CMFCVisualManager::OnDrawRibbonPanel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanel)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|重写[CMFCVisualManager::OnDrawRibbonPanelCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanelcaption)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|重写[CMFCVisualManager::OnDrawRibbonProgressBar](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|重写[CMFCVisualManager::OnDrawRibbonRecentFilesFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonrecentfilesframe)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|重写[CMFCVisualManager::OnDrawRibbonSliderChannel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|重写[CMFCVisualManager::OnDrawRibbonSliderThumb](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|重写[CMFCVisualManager::OnDrawRibbonSliderZoomButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|重写[CMFCVisualManager::OnDrawRibbonStatusBarPane](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonstatusbarpane)|  
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|重写[CMFCVisualManager::OnDrawRibbonTabsFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbontabsframe)|  
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|重写[CMFCVisualManagerWindows::OnDrawStatusBarSizeBox](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawstatusbarsizebox)|  
|`CMFCVisualManagerWindows7::OnFillBarBackground`|重写[CMFCVisualManagerWindows::OnFillBarBackground](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbarbackground)|  
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|重写[CMFCVisualManagerWindows::OnFillButtonInterior](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbuttoninterior)|  
|[CMFCVisualManagerWindows7::OnFillMenuImageRect](#onfillmenuimagerect)|当填充菜单项图像周围区域时，框架将调用此方法。|  
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|重写[CMFCVisualManager::OnFillRibbonButton](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonbutton)|  
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|重写[CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonquickaccesstoolbarpopup)|  
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|重写[CMFCVisualManagerWindows::OnHighlightMenuItem](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onhighlightmenuitem)|  
|`CMFCVisualManagerWindows7::OnNcActivate`|重写[CMFCVisualManager::OnNcActivate](../../mfc/reference/cmfcvisualmanager-class.md#onncactivate)|  
|`CMFCVisualManagerWindows7::OnNcPaint`|重写[CMFCVisualManager::OnNcPaint](../../mfc/reference/cmfcvisualmanager-class.md#onncpaint)|  
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|重写[CMFCVisualManagerWindows::OnUpdateSystemColors](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onupdatesystemcolors)|  
|`CMFCVisualManagerWindows7::SetResourceHandle`|设置描述视觉管理器的属性的资源句柄。|  
|`CMFCVisualManagerWindows7::SetStyle`|设置的配色方案`CMFCVisualManagerWindows7`GUI。|  
  
## <a name="remarks"></a>备注  
 使用`CMFCVisualManagerWindows7`类更改你的应用程序模拟默认外观[!INCLUDE[win7](../../build/includes/win7_md.md)]应用程序。 此类可能不是有效的 Windows 版本上运行你的应用程序如果早于[!INCLUDE[win7](../../build/includes/win7_md.md)]。 在这种情况下，应用程序使用默认视觉管理器中定义[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)。  
  
 CMFCVisualManagerWindows7 继承自多个方法[CMFCVisualManagerWindows 类](../../mfc/reference/cmfcvisualmanagerwindows-class.md)和`CMFCVisualManager`类。 上一节中列出的方法是方法的新手`CMFCVisualManagerWindows7`类。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)  
  
 `CMFCVisualManagerWindows7`  
  
## <a name="requirements"></a>要求  
 **标头：** afxvisualmanagerwindows7.h  
  
##  <a name="_dtorcmfcvisualmanagerwindows7"></a>  CMFCVisualManagerWindows7:: ~ CMFCVisualManagerWindows7  
 在默认析构函数。  
  
```  
virtual ~CMFCVisualManagerWindows7();
```  
  
##  <a name="cmfcvisualmanagerwindows7"></a>  CMFCVisualManagerWindows7::CMFCVisualManagerWindows7  
 默认构造函数。  
  
```  
CMFCVisualManagerWindows7();
```  
  
##  <a name="getribboneditbackgroundcolor"></a>  CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor  
 获取功能区编辑框的背景色。  
  
```  
virtual COLORREF GetRibbonEditBackgroundColor (
    CMFCRibbonRichEditCtrl* pEdit,  
    BOOL bIsHighlighted,  
    BOOL bIsPaneHighlighted,  
    BOOL bIsDisabled);
```  
  
### <a name="parameters"></a>参数  
 [in] `pEdit`  
 指向编辑控件的指针。 此值不能为 `NULL`。  
  
 [out] `bIsHighlighted`  
 返回功能区框中将突出显示。  
  
 [out] `bIsPaneHighlighted`  
 返回`TRUE`功能区面板中，如果包含`pEdit`突出显示。  
  
 [out] `bIsDisabled`  
 返回是否`pEdit`处于禁用状态。  
  
### <a name="return-value"></a>返回值  
 编辑框的背景色`pEdit`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onfillmenuimagerect"></a>  CMFCVisualManagerWindows7::OnFillMenuImageRect  
 当填充菜单项图像周围的区域时，框架将调用此方法。  
  
```  
virtual void OnFillMenuImageRect(
    CDC* pDC,  
    CMFCToolBarButton* pButton,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向菜单按钮的设备上下文的指针。  
  
 [in] `pButton`  
 指向的指针`CMFCToolBarButton`。 框架填充此按钮的背景。  
  
 [in] `rect`  
 指定菜单按钮图像区域的边界矩形。  
  
 [in] `state`  
 按钮的状态。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager 类](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerWindows 类](../../mfc/reference/cmfcvisualmanagerwindows-class.md)
