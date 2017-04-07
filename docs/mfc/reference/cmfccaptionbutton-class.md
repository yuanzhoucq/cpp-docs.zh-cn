---
title: "CMFCCaptionButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCCaptionButton class
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
caps.latest.revision: 28
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
ms.openlocfilehash: 9d6342f87622c34b671ad5ea443eb78ffd8c3838
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton 类
`CMFCCaptionButton`类实现在停靠窗格或微型框架窗口的标题栏显示的按钮。 通常，框架会自动创建标题按钮。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCCaptionButton : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="constructors"></a>构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|构造 CMFCCaptionButton 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCCaptionButton::GetHit](#gethit)|返回由按钮的命令。|  
|[CMFCCaptionButton::GetIconID](#geticonid)|返回与该按钮关联的图像 ID。|  
|[CMFCCaptionButton::GetRect](#getrect)|返回由按钮所占用的矩形。|  
|[CMFCCaptionButton::GetSize](#getsize)|返回的宽度和高度按钮。|  
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|指示是否为最小大小设置的标题栏的高度。|  
|[CMFCCaptionButton::Move](#move)|设置按钮绘图位置和窗口显示状态。|  
|[CMFCCaptionButton::OnDraw](#ondraw)|绘制标题按钮。|  
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|设置标题栏的最小大小。|  
  
## <a name="remarks"></a>备注  
 您可以从派生类[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)，并使用受保护的方法， `AddButton`，要添加到微型框架窗口的标题按钮。  
  
 CPaneFrameWnd.h 定义了两种类型的标题按钮的命令 Id:  
  
- `AFX_CAPTION_BTN_PIN`其中显示图钉按钮，在停靠窗格支持自动隐藏模式时。  
  
- `AFX_CAPTION_BTN_CLOSE`其中显示**关闭**按钮可以关闭或隐藏窗格。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCCaptionButton`对象，并将标题栏的最小大小。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&43;](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxcaptionbutton.h  
  
##  <a name="cmfccaptionbutton"></a>CMFCCaptionButton::CMFCCaptionButton  
 构造 `CMFCCaptionButton` 对象。  
  
```  
CMFCCaptionButton();

 
CMFCCaptionButton(
    UINT nHit,  
    BOOL bLeftAlign = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nHit`  
 与此按钮关联的命令。  
  
 [in] `bLeftAlign`  
 指定是否向左对齐按钮。  
  
 下表列出的可能值为`nHit`参数。  
  
|值|命令|  
|-----------|-------------|  
|`AFX_HTCLOSE`|关闭按钮。|  
|`HTMINBUTTON`|最小化按钮。|  
|`HTMAXBUTTON`|最大化按钮。|  
|`AFX_HTLEFTBUTTON`|左的箭头按钮。|  
|`AFX_HTRIGHTBUTTON`|向右箭头按钮。|  
|`AFX_HTMENU`|向下箭头菜单按钮。|  
|`HTNOWHERE`|默认值;不表示任何命令。|  
  
### <a name="remarks"></a>备注  
 默认情况下，标题按钮不与命令相关联。  
  
 标题按钮上的右侧或左侧对齐。  
  
##  <a name="gethit"></a>CMFCCaptionButton::GetHit  
 返回由按钮的命令。  
  
```  
UINT GetHit() const;  
```  
  
### <a name="return-value"></a>返回值  
 表示按钮的命令。  
  
 下表列出可能的返回值。  
  
|值|命令|  
|-----------|-------------|  
|`AFX_HTCLOSE`|关闭按钮。|  
|`HTMINBUTTON`|最小化按钮。|  
|`HTMAXBUTTON`|最大化按钮。|  
|`AFX_HTLEFTBUTTON`|左的箭头按钮。|  
|`AFX_HTRIGHTBUTTON`|向右箭头按钮。|  
|`AFX_HTMENU`|向下箭头菜单按钮。|  
|`HTNOWHERE`|默认值;不表示任何命令。|  
  
##  <a name="geticonid"></a>CMFCCaptionButton::GetIconID  
 返回与该按钮关联的图像 ID。  
  
```  
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,  
    BOOL bMaximized = FALSE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `bHorz`  
 `TRUE`对于左或向右箭头图像 Id。`FALSE`为向上或向下箭头图像 Id。  
  
 [in] `bMaximized`  
 `TRUE`最大化图像 ID。`FALSE`的最小化图像 id。  
  
### <a name="return-value"></a>返回值  
 图像 id。  
  
### <a name="remarks"></a>备注  
 参数指定最小化的图像 Id 或最大化标题按钮。  
  
##  <a name="getrect"></a>CMFCCaptionButton::GetRect  
 返回由按钮所占用的矩形。  
  
```  
virtual CRect GetRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 表示按钮的位置的矩形。  
  
### <a name="remarks"></a>备注  
 如果看不到按钮，返回的大小为 0。  
  
##  <a name="getsize"></a>CMFCCaptionButton::GetSize  
 返回的宽度和高度按钮。  
  
```  
static CSize GetSize();
```  
  
### <a name="return-value"></a>返回值  
 外部按钮的尺寸。  
  
### <a name="remarks"></a>备注  
 返回的大小包括按钮边距和边框。  
  
##  <a name="isminiframebutton"></a>CMFCCaptionButton::IsMiniFrameButton  
 指示是否为最小大小设置的标题栏的高度。  
  
```  
BOOL IsMiniFrameButton() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果标题设置为最小大小不同。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="move"></a>CMFCCaptionButton::Move  
 设置按钮绘图位置和窗口显示状态。  
  
```  
void Move(
    const CPoint& ptTo,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `ptTo`  
 新位置。  
  
 [in] `bHide`  
 是否显示按钮。  
  
##  <a name="ondraw"></a>CMFCCaptionButton::OnDraw  
 绘制标题按钮。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    BOOL bActive,  
    BOOL bHorz = TRUE,  
    BOOL bMaximized = TRUE,  
    BOOL bDisabled = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 按钮的设备上下文的指针。  
  
 [in] `bActive`  
 是否要绘制活动按钮的图像。  
  
 [in] `bHorz`  
 保留供派生类中使用。  
  
 [in] `bMaximized`  
 是否要绘制最大化的按钮图像。  
  
 [in] `bDisabled`  
 是否要绘制启用的按钮的图像。  
  
### <a name="remarks"></a>备注  
 `bMaximized`参数按钮时最大化或最小化按钮。  
  
##  <a name="setminiframebutton"></a>CMFCCaptionButton::SetMiniFrameButton  
 设置标题栏的最小大小。  
  
```  
void SetMiniFramebutton(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 `TRUE`为最小的标题栏的高度;`FALSE`为默认标题栏的高度。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)

