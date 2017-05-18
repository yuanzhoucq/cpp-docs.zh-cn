---
title: "CAutoHideDockSite 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
dev_langs:
- C++
helpviewer_keywords:
- AllowShowOnPaneMenu method
- CAutoHideDockSite class
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
caps.latest.revision: 32
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 58beaa382a2ef04cfaee0fbcf63b9eef36831472
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite 类
`CAutoHideDockSite`扩展[CDockSite 类](../../mfc/reference/cdocksite-class.md)来实现自动隐藏停靠窗格。  
  
## <a name="syntax"></a>语法  
  
```  
class CAutoHideDockSite : public CDockSite  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|描述|  
|`CAutoHideDockSite::CAutoHideDockSite`|构造 `CAutoHideDockSite` 对象。|  
|`CAutoHideDockSite::~CAutoHideDockSite`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|描述|  
|`CAutoHideDockSite::AllowShowOnPaneMenu`|指示是否`CAutoHideDockSite`窗格中菜单上显示。|  
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|确定是否将一个基本的窗格中对象派生自[CMFCAutoHideBar 类](../../mfc/reference/cmfcautohidebar-class.md)。|  
|[CAutoHideDockSite::DockPane](#dockpane)|窗格停靠到此`CAuotHideDockSite`对象。|  
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|检索在屏幕坐标中的停靠站点的大小。|  
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|在将重新绘制窗格中`CAutoHideDockSite`带有全局边距和按钮间距。|  
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|设置停靠栏左侧的边距。|  
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|设置停靠栏右侧的边距。|  
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|调用[CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)上的对象`CAutoHideDockSite`。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|名称|说明|  
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|定义工具栏和停靠栏的边缘之间的空间的大小。 这一领域被指从左边的缘或上边缘，具体取决于停靠空间的对齐方式。|  
  
## <a name="remarks"></a>备注  
 当您调用[CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)，框架将自动创建`CAutoHideDockSite`对象。 在大多数情况下，您应该不需要实例化，或者直接使用此类。  
  
 停靠栏是停靠窗格的左侧与左侧的内容之间的差距[CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## <a name="example"></a>示例  
 下面的示例演示如何检索`CAutoHideDockSite`对象从`CMFCAutoHideBar`对象，以及如何设置停靠栏的左侧和右侧边距。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&29;](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头︰** afxautohidedocksite.h  
  
##  <a name="canacceptpane"></a>CAutoHideDockSite::CanAcceptPane  
 确定是否为基的窗格中[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象或派生自`CMFCAutoHideBar`。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pBar`|基本窗格中，测试框架。|  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`pBar`派生自`CMFCAutoHideBar`;`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 如果基窗格对象派生自`CMFCAutoHideBar`，它可以包含`CAutoHideDockSite`。  
  
##  <a name="dockpane"></a>CAutoHideDockSite::DockPane  
 窗格停靠到此[CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)对象。  
  
```  
virtual void DockPane(
    CPane* pWnd,  
    AFX_DOCK_METHOD dockMethod,  
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pWnd`|框架停靠窗格。|  
|[in] `dockMethod`|停靠窗格的选项。|  
|[in] `lpRect`|指定停靠窗格中的边界的矩形。|  
  
### <a name="remarks"></a>备注  
 默认实现不使用参数`dockMethod`，提供供将来使用。  
  
 如果`lpRect`是`NULL`，框架将窗格中，在停靠站点上的默认位置。 如果水平停靠站点，默认位置是停靠站点最左端。 否则，默认位置是在停靠站点的顶部。  
  
##  <a name="getalignrect"></a>CAutoHideDockSite::GetAlignRect  
 检索在屏幕坐标中的停靠站点的大小。  
  
```  
void GetAlignRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `rect`|对一个矩形的引用。 该方法将存储在此矩形的停靠站点的大小。|  
  
### <a name="remarks"></a>备注  
 矩形是对于可以调整的偏移量的边距，以便不会包含这些。  
  
##  <a name="m_nextraspace"></a>CAutoHideDockSite::m_nExtraSpace  
 边缘之间的间距大小[CAutoHideDockSite 类](../../mfc/reference/cautohidedocksite-class.md)和[CMFCAutoHideBar 类](../../mfc/reference/cmfcautohidebar-class.md)对象。  
  
```  
static int m_nExtraSpace;  
```  
  
### <a name="remarks"></a>备注  
 当`CMFCAutoHideBar`停靠在`CAutoHideDockSite`，它应该不占用整个停靠站点。 此全局变量控制向左或顶部边框之间的额外空间`CMFCAutoHideBar`和相应`CAutoHideDockSite`边缘。 是否使用顶部或左侧边缘取决于当前对齐方式。  
  
##  <a name="setoffsetleft"></a>CAutoHideDockSite::SetOffsetLeft  
 设置停靠栏左侧的边距。  
  
```  
void SetOffsetLeft(int nOffset);
```  
  
### <a name="parameters"></a>参数  
 [in] `nOffset`  
 新的偏移量。  
  
### <a name="remarks"></a>备注  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象的位置以静态方式在`CAutoHideDockSite`对象。 这意味着用户不能手动更改的位置`CMFCAutoHideBar`对象。 `SetOffsetLeft`方法控制最左侧的左侧之间的间距`CMFCAutoHideBar`左边缘`CAutoHideDockSite`。  
  
##  <a name="setoffsetright"></a>CAutoHideDockSite::SetOffsetRight  
 设置停靠栏右侧的边距。  
  
```  
void SetOffsetRight(int nOffset);
```  
  
### <a name="parameters"></a>参数  
 [in] `nOffset`  
 新的偏移量。  
  
### <a name="remarks"></a>备注  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象的位置以静态方式在`CAutoHideDockSite`对象。 这意味着用户不能手动更改的位置`CMFCAutoHideBar`对象。 `SetOffsetRight`方法控制右侧的最右边的内容之间的间距`CMFCAutoHideBar`左右两侧`CAutoHideDockSite`。  
  
##  <a name="repositionpanes"></a>CAutoHideDockSite::RepositionPanes  
 在重绘窗格[CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)。  
  
```  
virtual void RepositionPanes(CRect& rectNewClientArea);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `rectNewClientArea`|保留的值。|  
  
### <a name="remarks"></a>备注  
 默认实现不使用`rectNewClientArea`。 它将重新绘制带有全局工具栏上边距和按钮间距窗格。  
  
##  <a name="unsetautohidemode"></a>CAutoHideDockSite::UnSetAutoHideMode  
 调用[CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)停靠站点上的对象。  
  
```  
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pAutoHideToolbar`|一个指向[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象窗格位于`CAutoHideDockSite`。|  
  
### <a name="remarks"></a>备注  
 此方法中包含的行的搜索`pAutoHideToolbar`。 它将调用`CMFCAutoHideBar.UnSetAutoHideMode`所有`CMFCAutoHideBar`在该行上的对象。 如果`pAutoHideToolbar`找不到或者它是`NULL`，此方法调用`CMFCAutoHideBar.UnSetAutoHideMode`所有`CMFCAutoHideBar`上的对象`CAutoHideDockSite`。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockSite 类](../../mfc/reference/cdocksite-class.md)

