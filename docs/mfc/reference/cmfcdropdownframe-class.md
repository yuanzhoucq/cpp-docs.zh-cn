---
title: "CMFCDropDownFrame 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownFrame class
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
caps.latest.revision: 23
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
ms.openlocfilehash: 5f045e4a3b580f12e64758737495c32963bea6db
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame 类
提供与下拉工具栏和下拉工具栏按钮的下拉列表框架窗口功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCDropDownFrame : public CMiniFrameWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|`CMFCDropDownFrame::CMFCDropDownFrame`|默认构造函数。|  
|`CMFCDropDownFrame::~CMFCDropDownFrame`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCDropDownFrame::Create](#create)|创建一个 `CMFCDropDownFrame` 对象。|  
|`CMFCDropDownFrame::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|检索父菜单栏中的下拉列表框。|  
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|检索父弹出菜单的下拉列表框。|  
|`CMFCDropDownFrame::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|重新定位下拉列表框。|  
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|设置是否自动销毁子下拉工具栏窗口。|  
  
### <a name="remarks"></a>备注  
 此类不应在代码中直接使用。  
  
 框架将使用此类提供对帧行为`CMFCDropDownToolbar`和`CMFCDropDownToolbarButton`类。 有关这些类的详细信息，请参阅[CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)和[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何检索一个指向`CMFCDropDownFrame`对象从`CFrameWnd`类，以及如何设置子下拉工具栏窗口，以自动将其销毁。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&36;](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxdropdowntoolbar.h  
  
##  <a name="create"></a>CMFCDropDownFrame::Create  
 创建一个 `CMFCDropDownFrame` 对象。  
  
```  
virtual BOOL Create(
    CWnd* pWndParent,  
    int x,  
    int y,  
    CMFCDropDownToolBar* pWndOriginToolbar);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pWndParent`|下拉列表框的父窗口。|  
|[in] `x`|向下下拉帧的位置水平屏幕坐标。|  
|[in] `y`|向下下拉帧的位置垂直屏幕坐标。|  
|[in] `pWndOriginToolbar`|具有此方法用于填充新的下拉列表框对象下拉列表按钮工具栏。|  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功创建下拉列表框;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法调用了基[CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法来创建与下拉列表框架窗口`WS_POPUP`样式。 下拉列表框架窗口将显示在指定的屏幕坐标。 如果此方法将失败[CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法将返回`FALSE`。  
  
 `CMFCDropDownFrame`类会创建一份提供的`CMFCDropDownToolBar`参数。 此方法会复制按钮图像和按钮状态从`pWndOriginToolbar`参数`m_pWndOriginToolbar`数据成员。  
  
##  <a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar  
 检索父菜单栏中的下拉列表框。  
  
```  
CMFCMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向父菜单栏中的下拉列表框中，或`NULL`如果帧没有父级。  
  
### <a name="remarks"></a>备注  
 此方法检索父菜单栏从父按钮。 此方法返回`NULL`如果下拉列表框架都有没有父按钮或父按钮没有父菜单栏。  
  
##  <a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu  
 检索父弹出菜单的下拉列表框。  
  
```  
CMFCDropDownFrame* GetParentPopupMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 父下拉列表菜单的下拉列表框中，指向的指针或`NULL`如果帧没有父级。  
  
### <a name="remarks"></a>备注  
 此方法从父按钮检索父菜单。 此方法返回`NULL`如果下拉列表框架都有没有父按钮或父按钮没有父菜单。  
  
##  <a name="recalclayout"></a>CMFCDropDownFrame::RecalcLayout  
 重新定位下拉列表框。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `bNotify`|未使用。|  
  
### <a name="remarks"></a>备注  
 创建下拉列表框或调整父窗口时，框架将调用此方法。 此方法使用的位置和位于父窗口的大小计算的位置和下拉列表框的大小。  
  
##  <a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy  
 设置是否自动销毁子下拉工具栏窗口。  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bAutoDestroy`  
 `TRUE`若要自动销毁关联的下拉列表工具栏窗口中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果`bAutoDestroy`是`TRUE`，则`CMFCDropDownFrame`析构函数将销毁关联的下拉列表工具栏窗口中。 默认值为 `TRUE`。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

