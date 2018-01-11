---
title: "CAutoHideDockSite 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e8cc4e9158ae9ff2ef6fd4d48483aa5a75dd9617
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite 类
`CAutoHideDockSite`扩展[CDockSite 类](../../mfc/reference/cdocksite-class.md)实现自动隐藏停靠窗格。  
  
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
|`CAutoHideDockSite::AllowShowOnPaneMenu`|指示是否`CAutoHideDockSite`窗格菜单上显示。|  
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|确定是否将一个基本的窗格对象派生自[CMFCAutoHideBar 类](../../mfc/reference/cmfcautohidebar-class.md)。|  
|[CAutoHideDockSite::DockPane](#dockpane)|窗格停靠到此`CAuotHideDockSite`对象。|  
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|检索屏幕坐标中的停靠站点的大小。|  
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|在重绘窗格`CAutoHideDockSite`与全局边距和按钮间距。|  
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|设置停靠栏左侧的边距。|  
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|设置停靠栏右侧的边距。|  
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|调用[CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)针对上的对象`CAutoHideDockSite`。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|name|描述|  
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|定义工具栏和停靠栏的边缘之间的空间的大小。 此空间被指从左边的缘或的上边缘，具体取决于停靠空间的对齐方式。|  
  
## <a name="remarks"></a>备注  
 当调用[CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)，框架会自动创建`CAutoHideDockSite`对象。 在大多数情况下，你应该不需要实例化或直接使用此类。  
  
 停靠栏是停靠窗格的左侧与左侧的内容之间的差距[CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## <a name="example"></a>示例  
 下面的示例演示如何检索`CAutoHideDockSite`对象`CMFCAutoHideBar`对象，以及如何设置停靠栏的左侧和右侧边距。  
  
 [!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]  
  
## <a name="requirements"></a>惠?  
 **标头：** afxautohidedocksite.h  
  
##  <a name="canacceptpane"></a>CAutoHideDockSite::CanAcceptPane  
 确定是否为基的窗格中[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象或派生自`CMFCAutoHideBar`。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in] `pBar`|基本窗格中，测试框架。|  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`pBar`派生自`CMFCAutoHideBar`;`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 如果一个基窗格对象派生自`CMFCAutoHideBar`，它可以包含`CAutoHideDockSite`。  
  
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
|参数|描述|  
|[in] `pWnd`|框架停靠窗格。|  
|[in] `dockMethod`|停靠的窗格的选项。|  
|[in] `lpRect`|指定停靠的窗格的边界矩形。|  
  
### <a name="remarks"></a>备注  
 默认实现不使用参数`dockMethod`，提供供将来使用。  
  
 如果`lpRect`是`NULL`，框架将窗格放置在停靠站点上的默认位置。 如果水平停靠站点，默认位置是在最左侧的停靠站点。 否则，默认位置为在停靠站点的顶部。  
  
##  <a name="getalignrect"></a>CAutoHideDockSite::GetAlignRect  
 检索屏幕坐标中的停靠站点的大小。  
  
```  
void GetAlignRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in] `rect`|对一个矩形的引用。 该方法将存储在此矩形的停靠站点的大小。|  
  
### <a name="remarks"></a>备注  
 以便不会包含这些对于偏移量的边距调整矩形。  
  
##  <a name="m_nextraspace"></a>CAutoHideDockSite::m_nExtraSpace  
 边缘之间的间距大小[CAutoHideDockSite 类](../../mfc/reference/cautohidedocksite-class.md)和[CMFCAutoHideBar 类](../../mfc/reference/cmfcautohidebar-class.md)对象。  
  
```  
static int m_nExtraSpace;  
```  
  
### <a name="remarks"></a>备注  
 当`CMFCAutoHideBar`停靠在`CAutoHideDockSite`，它不应占用整个停靠站点。 此全局变量控制向左或顶部边框之间的额外空间`CMFCAutoHideBar`和相应`CAutoHideDockSite`边缘。 是否使用顶部或左侧边缘取决于当前对齐方式。  
  
##  <a name="setoffsetleft"></a>CAutoHideDockSite::SetOffsetLeft  
 设置停靠栏左侧的边距。  
  
```  
void SetOffsetLeft(int nOffset);
```  
  
### <a name="parameters"></a>参数  
 [in] `nOffset`  
 新的偏移量。  
  
### <a name="remarks"></a>备注  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象中的静态上放置`CAutoHideDockSite`对象。 这意味着用户无法手动更改的位置`CMFCAutoHideBar`对象。 `SetOffsetLeft`方法控制的最左侧左侧之间的间距`CMFCAutoHideBar`左边缘`CAutoHideDockSite`。  
  
##  <a name="setoffsetright"></a>CAutoHideDockSite::SetOffsetRight  
 设置停靠栏右侧的边距。  
  
```  
void SetOffsetRight(int nOffset);
```  
  
### <a name="parameters"></a>参数  
 [in] `nOffset`  
 新的偏移量。  
  
### <a name="remarks"></a>备注  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象中的静态上放置`CAutoHideDockSite`对象。 这意味着用户无法手动更改的位置`CMFCAutoHideBar`对象。 `SetOffsetRight`方法控制的最右边的右侧之间的间距`CMFCAutoHideBar`左右两侧`CAutoHideDockSite`。  
  
##  <a name="repositionpanes"></a>CAutoHideDockSite::RepositionPanes  
 在重绘窗格[CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)。  
  
```  
virtual void RepositionPanes(CRect& rectNewClientArea);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in] `rectNewClientArea`|保留的值。|  
  
### <a name="remarks"></a>备注  
 默认实现不使用`rectNewClientArea`。 它重绘全局工具栏上边距和按钮间距窗格。  
  
##  <a name="unsetautohidemode"></a>CAutoHideDockSite::UnSetAutoHideMode  
 调用[CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)针对停靠站点上的对象。  
  
```  
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in] `pAutoHideToolbar`|指向的指针[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)对象窗格位于`CAutoHideDockSite`。|  
  
### <a name="remarks"></a>备注  
 此方法搜索包含的行`pAutoHideToolbar`。 它调用`CMFCAutoHideBar.UnSetAutoHideMode`所有`CMFCAutoHideBar`该行上的对象。 如果`pAutoHideToolbar`找不到或者它是`NULL`，此方法调用`CMFCAutoHideBar.UnSetAutoHideMode`所有`CMFCAutoHideBar`对象上`CAutoHideDockSite`。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockSite 类](../../mfc/reference/cdocksite-class.md)
