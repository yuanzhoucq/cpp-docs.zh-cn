---
title: "CMFCRibbonButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonButton
- AFXRIBBONBUTTON/CMFCRibbonButton
- AFXRIBBONBUTTON/CMFCRibbonButton::CMFCRibbonButton
- AFXRIBBONBUTTON/CMFCRibbonButton::AddSubItem
- AFXRIBBONBUTTON/CMFCRibbonButton::CanBeStretched
- AFXRIBBONBUTTON/CMFCRibbonButton::CleanUpSizes
- AFXRIBBONBUTTON/CMFCRibbonButton::ClosePopupMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::DrawBottomText
- AFXRIBBONBUTTON/CMFCRibbonButton::DrawImage
- AFXRIBBONBUTTON/CMFCRibbonButton::DrawRibbonText
- AFXRIBBONBUTTON/CMFCRibbonButton::FindSubItemIndexByID
- AFXRIBBONBUTTON/CMFCRibbonButton::GetCommandRect
- AFXRIBBONBUTTON/CMFCRibbonButton::GetCompactSize
- AFXRIBBONBUTTON/CMFCRibbonButton::GetIcon
- AFXRIBBONBUTTON/CMFCRibbonButton::GetImageIndex
- AFXRIBBONBUTTON/CMFCRibbonButton::GetImageSize
- AFXRIBBONBUTTON/CMFCRibbonButton::GetIntermediateSize
- AFXRIBBONBUTTON/CMFCRibbonButton::GetMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::GetMenuRect
- AFXRIBBONBUTTON/CMFCRibbonButton::GetRegularSize
- AFXRIBBONBUTTON/CMFCRibbonButton::GetSubItems
- AFXRIBBONBUTTON/CMFCRibbonButton::GetTextRowHeight
- AFXRIBBONBUTTON/CMFCRibbonButton::GetToolTipText
- AFXRIBBONBUTTON/CMFCRibbonButton::HasCompactMode
- AFXRIBBONBUTTON/CMFCRibbonButton::HasIntermediateMode
- AFXRIBBONBUTTON/CMFCRibbonButton::HasLargeMode
- AFXRIBBONBUTTON/CMFCRibbonButton::HasMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::IsAlwaysDrawBorder
- AFXRIBBONBUTTON/CMFCRibbonButton::IsAlwaysLargeImage
- AFXRIBBONBUTTON/CMFCRibbonButton::IsApplicationButton
- AFXRIBBONBUTTON/CMFCRibbonButton::IsCommandAreaHighlighted
- AFXRIBBONBUTTON/CMFCRibbonButton::IsDefaultCommand
- AFXRIBBONBUTTON/CMFCRibbonButton::IsDefaultPanelButton
- AFXRIBBONBUTTON/CMFCRibbonButton::IsDrawTooltipImage
- AFXRIBBONBUTTON/CMFCRibbonButton::IsLargeImage
- AFXRIBBONBUTTON/CMFCRibbonButton::IsMenuAreaHighlighted
- AFXRIBBONBUTTON/CMFCRibbonButton::IsMenuOnBottom
- AFXRIBBONBUTTON/CMFCRibbonButton::IsPopupDefaultMenuLook
- AFXRIBBONBUTTON/CMFCRibbonButton::IsRightAlignMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::IsSingleLineText
- AFXRIBBONBUTTON/CMFCRibbonButton::OnCalcTextSize
- AFXRIBBONBUTTON/CMFCRibbonButton::OnDrawBorder
- AFXRIBBONBUTTON/CMFCRibbonButton::OnDraw
- AFXRIBBONBUTTON/CMFCRibbonButton::OnFillBackground
- AFXRIBBONBUTTON/CMFCRibbonButton::RemoveAllSubItems
- AFXRIBBONBUTTON/CMFCRibbonButton::RemoveSubItem
- AFXRIBBONBUTTON/CMFCRibbonButton::SetACCData
- AFXRIBBONBUTTON/CMFCRibbonButton::SetAlwaysLargeImage
- AFXRIBBONBUTTON/CMFCRibbonButton::SetDefaultCommand
- AFXRIBBONBUTTON/CMFCRibbonButton::SetDescription
- AFXRIBBONBUTTON/CMFCRibbonButton::SetImageIndex
- AFXRIBBONBUTTON/CMFCRibbonButton::SetMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::SetParentCategory
- AFXRIBBONBUTTON/CMFCRibbonButton::SetRightAlignMenu
- AFXRIBBONBUTTON/CMFCRibbonButton::SetText
- AFXRIBBONBUTTON/CMFCRibbonButton::OnClick
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonButton class
ms.assetid: 732e941c-9504-4b83-a691-d18075965d53
caps.latest.revision: 42
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
ms.openlocfilehash: 08672f10cf67a773f2af8d12130c4e3f5b497e11
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonbutton-class"></a>CMFCRibbonButton 类
`CMFCRibbonButton` 类实现可放置在功能区栏元素（例如面板、快速访问工具栏和弹出菜单）上的按钮。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonButton : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonButton::CMFCRibbonButton](#cmfcribbonbutton)|构造一个功能区按钮对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonButton::AddSubItem](#addsubitem)|将菜单项添加到与按钮相关联的弹出菜单。|  
|[CMFCRibbonButton::CanBeStretched](#canbestretched)|(重写[CMFCRibbonBaseElement::CanBeStretched](../../mfc/reference/cmfcribbonbaseelement-class.md#canbestretched)。)|  
|[CMFCRibbonButton::CleanUpSizes](#cleanupsizes)|(重写[CMFCRibbonBaseElement::CleanUpSizes](../../mfc/reference/cmfcribbonbaseelement-class.md#cleanupsizes)。)|  
|[CMFCRibbonButton::ClosePopupMenu](#closepopupmenu)|(重写[CMFCRibbonBaseElement::ClosePopupMenu](../../mfc/reference/cmfcribbonbaseelement-class.md#closepopupmenu)。)|  
|[CMFCRibbonButton::DrawBottomText](#drawbottomtext)||  
|[CMFCRibbonButton::DrawImage](#drawimage)|(重写[CMFCRibbonBaseElement::DrawImage](../../mfc/reference/cmfcribbonbaseelement-class.md#drawimage)。)|  
|[CMFCRibbonButton::DrawRibbonText](#drawribbontext)||  
|[CMFCRibbonButton::FindSubItemIndexByID](#findsubitemindexbyid)|返回与指定的命令 ID 相关联的弹出菜单项的索引。|  
|[CMFCRibbonButton::GetCommandRect](#getcommandrect)||  
|[CMFCRibbonButton::GetCompactSize](#getcompactsize)|返回功能区元素的压缩大小。 (重写[CMFCRibbonBaseElement::GetCompactSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getcompactsize)。)|  
|[CMFCRibbonButton::GetIcon](#geticon)||  
|[CMFCRibbonButton::GetImageIndex](#getimageindex)|返回与按钮相关联的图像的索引。|  
|[CMFCRibbonButton::GetImageSize](#getimagesize)|返回功能区元素的图像大小。 (重写[CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize)。)|  
|[CMFCRibbonButton::GetIntermediateSize](#getintermediatesize)|返回处于中间状态的功能区元素的大小。 (重写[CMFCRibbonBaseElement::GetIntermediateSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getintermediatesize)。)|  
|[CMFCRibbonButton::GetMenu](#getmenu)|将一个句柄返回给一个分配给功能区按钮的 Windows 菜单。|  
|[CMFCRibbonButton::GetMenuRect](#getmenurect)||  
|[CMFCRibbonButton::GetRegularSize](#getregularsize)|返回功能区元素的常规大小。 (重写[CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|  
|[CMFCRibbonButton::GetSubItems](#getsubitems)||  
|[CMFCRibbonButton::GetTextRowHeight](#gettextrowheight)||  
|[CMFCRibbonButton::GetToolTipText](#gettooltiptext)|返回功能区元素的工具提示文本。 (重写[CMFCRibbonBaseElement::GetToolTipText](../../mfc/reference/cmfcribbonbaseelement-class.md#gettooltiptext)。)|  
|[CMFCRibbonButton::HasCompactMode](#hascompactmode)|指定功能区元素是否有压缩模式。 (重写[CMFCRibbonBaseElement::HasCompactMode](../../mfc/reference/cmfcribbonbaseelement-class.md#hascompactmode)。)|  
|[CMFCRibbonButton::HasIntermediateMode](#hasintermediatemode)|指定功能区元素是否有中间模式。 (重写[CMFCRibbonBaseElement::HasIntermediateMode](../../mfc/reference/cmfcribbonbaseelement-class.md#hasintermediatemode)。)|  
|[CMFCRibbonButton::HasLargeMode](#haslargemode)|确定功能区元素是否有大型模式。 (重写[CMFCRibbonBaseElement::HasLargeMode](../../mfc/reference/cmfcribbonbaseelement-class.md#haslargemode)。)|  
|[CMFCRibbonButton::HasMenu](#hasmenu)|(重写[CMFCRibbonBaseElement::HasMenu](../../mfc/reference/cmfcribbonbaseelement-class.md#hasmenu)。)|  
|[CMFCRibbonButton::IsAlwaysDrawBorder](#isalwaysdrawborder)||  
|[CMFCRibbonButton::IsAlwaysLargeImage](#isalwayslargeimage)|(重写[CMFCRibbonBaseElement::IsAlwaysLargeImage](../../mfc/reference/cmfcribbonbaseelement-class.md#isalwayslargeimage)。)|  
|[CMFCRibbonButton::IsApplicationButton](#isapplicationbutton)||  
|[CMFCRibbonButton::IsCommandAreaHighlighted](#iscommandareahighlighted)||  
|[CMFCRibbonButton::IsDefaultCommand](#isdefaultcommand)|确定是否已启用功能区按钮的默认命令。|  
|[CMFCRibbonButton::IsDefaultPanelButton](#isdefaultpanelbutton)||  
|[CMFCRibbonButton::IsDrawTooltipImage](#isdrawtooltipimage)||  
|[CMFCRibbonButton::IsLargeImage](#islargeimage)||  
|[CMFCRibbonButton::IsMenuAreaHighlighted](#ismenuareahighlighted)||  
|[CMFCRibbonButton::IsMenuOnBottom](#ismenuonbottom)||  
|[CMFCRibbonButton::IsPopupDefaultMenuLook](#ispopupdefaultmenulook)||  
|[CMFCRibbonButton::IsRightAlignMenu](#isrightalignmenu)|确定菜单是否为右对齐。|  
|[CMFCRibbonButton::IsSingleLineText](#issinglelinetext)||  
|[CMFCRibbonButton::OnCalcTextSize](#oncalctextsize)|(重写[CMFCRibbonBaseElement::OnCalcTextSize](../../mfc/reference/cmfcribbonbaseelement-class.md#oncalctextsize)。)|  
|[CMFCRibbonButton::OnDrawBorder](#ondrawborder)||  
|[CMFCRibbonButton::OnDraw](#ondraw)|由框架调用以绘制功能区元素。 (重写[CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)。)|  
|[CMFCRibbonButton::OnFillBackground](#onfillbackground)||  
|[CMFCRibbonButton::RemoveAllSubItems](#removeallsubitems)|从弹出菜单中删除所有菜单项。|  
|[CMFCRibbonButton::RemoveSubItem](#removesubitem)|从弹出菜单中删除一个菜单项。|  
|[CMFCRibbonButton::SetACCData](#setaccdata)|(重写[CMFCRibbonBaseElement::SetACCData](../../mfc/reference/cmfcribbonbaseelement-class.md#setaccdata)。)|  
|[CMFCRibbonButton::SetAlwaysLargeImage](#setalwayslargeimage)|指定当用户折叠按钮时，按钮显示大图像还是小图像。|  
|[CMFCRibbonButton::SetDefaultCommand](#setdefaultcommand)|启用功能区按钮的默认命令。|  
|[CMFCRibbonButton::SetDescription](#setdescription)|设置功能区元素的说明。 (重写[CMFCRibbonBaseElement::SetDescription](../../mfc/reference/cmfcribbonbaseelement-class.md#setdescription)。)|  
|[CMFCRibbonButton::SetImageIndex](#setimageindex)|将索引分配给按钮的图像。|  
|[CMFCRibbonButton::SetMenu](#setmenu)|将弹出菜单分配给功能区按钮。|  
|[CMFCRibbonButton::SetParentCategory](#setparentcategory)|(重写[CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory)。)|  
|[CMFCRibbonButton::SetRightAlignMenu](#setrightalignmenu)|使弹出菜单与按钮的右侧对齐。|  
|[CMFCRibbonButton::SetText](#settext)|设置功能区元素的文本。 (重写[CMFCRibbonBaseElement::SetText](../../mfc/reference/cmfcribbonbaseelement-class.md#settext)。)|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonButton::OnClick](#onclick)|当用户单击按钮时，由框架调用。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 `CMFCRibbonButton` 类中的各种方法。 该示例展示如何构造 `CMFCRibbonButton` 类的对象，将弹出菜单分配给功能区按钮，设置按钮的说明，从弹出菜单中删除一个菜单项，然后使弹出菜单与按钮的边缘右对齐。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&7;](../../mfc/reference/codesnippet/cpp/cmfcribbonbutton-class_1.cpp)]  
  
## <a name="remarks"></a>备注  
 若要在应用程序中使用的功能区按钮，构造按钮对象并将其添加到相应的功能区[面板](../../mfc/reference/cmfcribbonpanel-class.md)。  
  
```  
CMFCRibbonPanel* pPanel = pCategory->AddPanel (
    _T("Clipboard"), // Panel name  
    m_PanelIcons.ExtractIcon (0)); // Panel icon  

// Create the first button ("Paste"):  
CMFCRibbonButton* pPasteButton = 
    new CMFCRibbonButton (ID_EDIT_PASTE, _T("Paste"), -1, 0);

// The third parameter (-1) disables small images for button.  
// This button is always displayed with a large image  
// Associate a pop-up menu with the "Paste" button:  
pPasteButton->SetMenu (IDR_CONTEXT_MENU);

// Add buttons to the panel. These buttons have only small images.  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_CUT, _T("Cut"), 1));
pPanel->Add (new CMFCRibbonButton (ID_EDIT_COPY, _T("Copy"), 2));
pPanel->Add (new CMFCRibbonButton (ID_EDIT_PAINT, _T("Paint"), 9));
```  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxribbonbutton.h  
  
##  <a name="addsubitem"></a>CMFCRibbonButton::AddSubItem  
 将菜单项添加到与按钮相关联的弹出菜单。  
  
```  
void AddSubItem(
    CMFCRibbonBaseElement* pSubItem,  
    int nIndex=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `pSubItem`  
 指定指向要添加的新元素的指针。  
  
 [in] `nIndex`  
 指定用于将元素添加到的菜单项的按钮，则数组的索引为-1 的菜单项的数组的末尾添加元素。  
  
##  <a name="canbestretched"></a>CMFCRibbonButton::CanBeStretched  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="cleanupsizes"></a>CMFCRibbonButton::CleanUpSizes  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CleanUpSizes();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="closepopupmenu"></a>CMFCRibbonButton::ClosePopupMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ClosePopupMenu();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="cmfcribbonbutton"></a>CMFCRibbonButton::CMFCRibbonButton  
 构造一个功能区按钮对象。  
  
```  
CMFCRibbonButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex=-1,  
    int nLargeImageIndex=-1,  
    BOOL bAlwaysShowDescription=FALSE);

CMFCRibbonButton(
    UINT nID,  
    LPCTSTR lpszText,  
    HICON hIcon,  
    BOOL bAlwaysShowDescription=FALSE,  
    HICON hIconSmall=NULL,  
    BOOL bAutoDestroyIcon=FALSE,  
    BOOL bAlphaBlendIcon=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 指定按钮的命令 ID。  
  
 [in] `lpszText`  
 指定按钮的文本标签。  
  
 [in] `nSmallImageIndex`  
 指定父类别的图像列表中的按钮的小图像的从零开始索引。  
  
 [in] `nLargeImageIndex`  
 指定父类别的图像列表中的按钮的大图像的从零开始索引。  
  
 [in] `hIcon`  
 指定应用程序用作按钮的图像的图标的句柄。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCRibbonButton`对象。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&6;](../../mfc/reference/codesnippet/cpp/cmfcribbonbutton-class_2.cpp)]  
  
##  <a name="drawbottomtext"></a>CMFCRibbonButton::DrawBottomText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CSize DrawBottomText(
    CDC* pDC,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 [in] `bCalcOnly`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="drawimage"></a>CMFCRibbonButton::DrawImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void DrawImage(
    CDC* pDC,  
    RibbonImageType type,  
    CRect rectImage);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 [in] `type`  
 [in] `rectImage`  
  
### <a name="remarks"></a>备注  
  
##  <a name="drawribbontext"></a>CMFCRibbonButton::DrawRibbonText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int DrawRibbonText(
    CDC* pDC,  
    const CString& strText,  
    CRect rectText,  
    UINT uiDTFlags,  
    COLORREF clrText = (COLORREF)-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 [in] `strText`  
 [in] `rectText`  
 [in] `uiDTFlags`  
 [in] `clrText`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="findsubitemindexbyid"></a>CMFCRibbonButton::FindSubItemIndexByID  
 返回与指定的命令 ID 相关联的弹出菜单项的索引。  
  
```  
int FindSubItemIndexByID(UINT uiID) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
 指定弹出菜单项的命令 ID。  
  
### <a name="return-value"></a>返回值  
 与之关联的子项的从零开始索引`uiID`。 如果没有此类子项目，则为-1。  
  
##  <a name="getcommandrect"></a>CMFCRibbonButton::GetCommandRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetCommandRect() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcompactsize"></a>CMFCRibbonButton::GetCompactSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="geticon"></a>CMFCRibbonButton::GetIcon  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
HICON GetIcon(BOOL bLargeIcon = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `bLargeIcon`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getimageindex"></a>CMFCRibbonButton::GetImageIndex  
 返回与按钮相关联的图像的索引。  
  
```  
int GetImageIndex(BOOL bLargeImage) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `bLargeImage`  
 如果`TRUE`，返回包含大型图像; 否则返回的图像索引包含较小的图像的图像列表中的图像列表中的图像索引。  
  
### <a name="return-value"></a>返回值  
 在关联的图像列表中的按钮的图像的索引。  
  
##  <a name="getimagesize"></a>CMFCRibbonButton::GetImageSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetImageSize(RibbonImageType type) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `type`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getintermediatesize"></a>CMFCRibbonButton::GetIntermediateSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getmenu"></a>CMFCRibbonButton::GetMenu  
 将一个句柄返回给一个分配给功能区按钮的 Windows 菜单。  
  
```  
HMENU GetMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 分配给按钮; 一个 Windows 菜单句柄`NULL`如果没有分配任何菜单。  
  
##  <a name="getmenurect"></a>CMFCRibbonButton::GetMenuRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetMenuRect() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getregularsize"></a>CMFCRibbonButton::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getsubitems"></a>CMFCRibbonButton::GetSubItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
const CArray<CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& GetSubItems() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettextrowheight"></a>CMFCRibbonButton::GetTextRowHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTextRowHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettooltiptext"></a>CMFCRibbonButton::GetToolTipText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CString GetToolTipText() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="hascompactmode"></a>CMFCRibbonButton::HasCompactMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="hasintermediatemode"></a>CMFCRibbonButton::HasIntermediateMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasIntermediateMode() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="haslargemode"></a>CMFCRibbonButton::HasLargeMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="hasmenu"></a>CMFCRibbonButton::HasMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isalwaysdrawborder"></a>CMFCRibbonButton::IsAlwaysDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsAlwaysDrawBorder() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isalwayslargeimage"></a>CMFCRibbonButton::IsAlwaysLargeImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsAlwaysLargeImage() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isapplicationbutton"></a>CMFCRibbonButton::IsApplicationButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsApplicationButton() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="iscommandareahighlighted"></a>CMFCRibbonButton::IsCommandAreaHighlighted  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsCommandAreaHighlighted() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isdefaultcommand"></a>CMFCRibbonButton::IsDefaultCommand  
 指定是否启用的功能区按钮的默认命令。  
  
```  
BOOL IsDefaultCommand() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已启用的功能区按钮; 默认命令`FALSE`否则为。  
  
##  <a name="isdefaultpanelbutton"></a>CMFCRibbonButton::IsDefaultPanelButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsDefaultPanelButton() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isdrawtooltipimage"></a>CMFCRibbonButton::IsDrawTooltipImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="islargeimage"></a>CMFCRibbonButton::IsLargeImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsLargeImage() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ismenuareahighlighted"></a>CMFCRibbonButton::IsMenuAreaHighlighted  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsMenuAreaHighlighted() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ismenuonbottom"></a>CMFCRibbonButton::IsMenuOnBottom  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMenuOnBottom() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ispopupdefaultmenulook"></a>CMFCRibbonButton::IsPopupDefaultMenuLook  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsPopupDefaultMenuLook() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isrightalignmenu"></a>CMFCRibbonButton::IsRightAlignMenu  
 指定菜单中是否为右对齐。  
  
```  
BOOL IsRightAlignMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果菜单为右对齐;否则为`FALSE`。  
  
##  <a name="issinglelinetext"></a>CMFCRibbonButton::IsSingleLineText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsSingleLineText() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="oncalctextsize"></a>CMFCRibbonButton::OnCalcTextSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnCalcTextSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onclick"></a>CMFCRibbonButton::OnClick  
 当用户单击按钮时，由框架调用。  
  
```  
virtual void OnClick(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 指定鼠标单击的位置。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类中的，如果你想要处理此事件。  
  
##  <a name="ondraw"></a>CMFCRibbonButton::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawborder"></a>CMFCRibbonButton::OnDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawBorder(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onfillbackground"></a>CMFCRibbonButton::OnFillBackground  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="removeallsubitems"></a>CMFCRibbonButton::RemoveAllSubItems  
 从弹出菜单中删除所有菜单项。  
  
```  
void RemoveAllSubItems();
```  
  
##  <a name="removesubitem"></a>CMFCRibbonButton::RemoveSubItem  
 从弹出菜单中删除一个菜单项。  
  
```  
BOOL RemoveSubItem(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定你想要删除的菜单项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功，则删除指定的项否则为`FALSE`如果`nIndex`为负或超过的弹出菜单中的菜单项的数目。  
  
##  <a name="setaccdata"></a>CMFCRibbonButton::SetACCData  
 设置功能区按钮的辅助功能数据。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);  
```  
  
### <a name="parameters"></a>参数  
 `pParent`  
 功能区元素的父窗口。  
  
 `data`  
 功能区元素的可访问性数据。  
  
### <a name="return-value"></a>返回值  
 如果成功则返回 `TRUE` ；否则返回 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setalwayslargeimage"></a>CMFCRibbonButton::SetAlwaysLargeImage  
 指定当用户折叠按钮时，按钮显示大图像还是小图像。  
  
```  
void SetAlwaysLargeImage(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 如果`TRUE`，按钮将显示一个大图像。 否则，该按钮显示的小图像。  
  
##  <a name="setdefaultcommand"></a>CMFCRibbonButton::SetDefaultCommand  
 启用功能区按钮的默认命令。  
  
```  
void SetDefaultCommand(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 如果`TRUE`，按钮可以执行其默认命令。 如果`FALSE`，按钮不能执行其默认命令。  
  
### <a name="remarks"></a>备注  
 `bSet`仅当按钮具有一个菜单时才是相关。 如果`bSet`是`TRUE`按钮可以执行其默认命令，仅当用户单击该按钮的右边缘的箭头，则显示已分配的弹出菜单。 否则为按钮不能执行其默认的命令，并弹出菜单显示在用户单击而不考虑按钮的区域。  
  
##  <a name="setdescription"></a>CMFCRibbonButton::SetDescription  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetDescription(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszText`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setimageindex"></a>CMFCRibbonButton::SetImageIndex  
 将索引分配给按钮的图像。  
  
```  
void SetImageIndex(
    int nIndex,  
    BOOL bLargeImage);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 指定的图像索引。  
  
 [in] `bLargeImage`  
 如果`TRUE`，指定的索引引用了大图像列表。 否则，索引引用的较小的图像列表。  
  
##  <a name="setmenu"></a>CMFCRibbonButton::SetMenu  
 将弹出菜单分配给功能区按钮。  
  
```  
void SetMenu(
    HMENU hMenu,  
    BOOL bIsDefaultCommand=FALSE,  
    BOOL bRightAlign=FALSE);

void SetMenu(
    UINT uiMenuResID,  
    BOOL bIsDefaultCommand=FALSE,  
    BOOL bRightAlign=FALSE);
```  
  
### <a name="parameters"></a>参数  
 `hMenu`  
 Windows 菜单句柄。  
  
 `bIsDefaultCommand`  
 如果`TRUE`，按钮可以执行其默认命令; 否则，按钮将显示一个弹出菜单。  
  
 `bRightAlign`  
 如果`TRUE`，菜单是右对齐。 否则，菜单是左对齐。  
  
 `uiMenuResID`  
 菜单上的资源 id。  
  
### <a name="remarks"></a>备注  
 当应用程序将分配给按钮的菜单上时，按钮将显示在其右侧的箭头。 如果`bIsDefaultCommand`是`TRUE`，仅当用户单击箭头将显示的菜单。 如果用户单击按钮时，将执行其默认命令。 如果`bIsDefaultCommand`是`FALSE`，通过单击任意位置的按钮将显示的菜单。  
  
##  <a name="setparentcategory"></a>CMFCRibbonButton::SetParentCategory  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetParentCategory(CMFCRibbonCategory* pParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParent`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setrightalignmenu"></a>CMFCRibbonButton::SetRightAlignMenu  
 将弹出菜单按钮的边缘对齐。  
  
```  
void SetRightAlignMenu(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 如果`TRUE`，菜单是右对齐。 否则，菜单是左对齐  
  
##  <a name="settext"></a>CMFCRibbonButton::SetText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszText`  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)

