---
title: CMFCDropDownFrame 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c7264273f3db1dab1e6cab72333c0629a802e28
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041989"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame 类
下拉列表框架窗口功能提供给下拉工具栏和下拉工具栏按钮。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCDropDownFrame : public CMiniFrameWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|描述|  
|`CMFCDropDownFrame::CMFCDropDownFrame`|默认构造函数。|  
|`CMFCDropDownFrame::~CMFCDropDownFrame`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCDropDownFrame::Create](#create)|创建一个 `CMFCDropDownFrame` 对象。|  
|`CMFCDropDownFrame::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|检索父菜单栏中的下拉菜单的帧。|  
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|检索父弹出菜单的下拉列表框。|  
|`CMFCDropDownFrame::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|将重新定位的下拉菜单的帧。|  
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|设置是否自动销毁子下拉工具栏窗口。|  
  
### <a name="remarks"></a>备注  
 此类不应在代码中直接使用。  
  
 框架将使用此类提供到的帧行为`CMFCDropDownToolbar`和`CMFCDropDownToolbarButton`类。 有关这些类的详细信息，请参阅[CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)和[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何检索一个指向`CMFCDropDownFrame`对象`CFrameWnd`类，以及如何子下拉工具栏将窗口设置为自动销毁。  
  
 [!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxdropdowntoolbar.h  
  
##  <a name="create"></a>  CMFCDropDownFrame::Create  
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
|参数|描述|  
|[in]*pWndParent*|下拉列表框架的父窗口。|  
|[in]*x*|向下取帧的位置水平屏幕坐标。|  
|[in]*y*|向下取帧的位置垂直屏幕坐标。|  
|[in]*pWndOriginToolbar*|具有此方法用于填充新的下拉列表框架对象的下拉列表按钮的工具栏。|  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果已成功创建下拉帧;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法调用了基[CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法来创建与下拉列表框架窗口`WS_POPUP`样式。 下拉列表框架窗口将显示在指定的屏幕坐标。 如果此方法将失败[CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法返回`FALSE`。  
  
 `CMFCDropDownFrame`类会创建一份提供的`CMFCDropDownToolBar`参数。 此方法会复制按钮图像和按钮状态从`pWndOriginToolbar`参数`m_pWndOriginToolbar`数据成员。  
  
##  <a name="getparentmenubar"></a>  CMFCDropDownFrame::GetParentMenuBar  
 检索父菜单栏中的下拉菜单的帧。  
  
```  
CMFCMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 下拉列表框中，父菜单栏的指针或`NULL`如果帧没有父级。  
  
### <a name="remarks"></a>备注  
 此方法从父按钮检索父菜单栏。 此方法返回`NULL`如果下拉列表框架都有没有父按钮或父按钮有任何父菜单栏。  
  
##  <a name="getparentpopupmenu"></a>  CMFCDropDownFrame::GetParentPopupMenu  
 检索父弹出菜单的下拉列表框。  
  
```  
CMFCDropDownFrame* GetParentPopupMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 下拉列表框中，父下拉列表菜单的指针或`NULL`如果帧没有父级。  
  
### <a name="remarks"></a>备注  
 此方法检索父菜单从父按钮。 此方法返回`NULL`如果下拉列表框架都有没有父按钮或父按钮有任何父菜单。  
  
##  <a name="recalclayout"></a>  CMFCDropDownFrame::RecalcLayout  
 将重新定位的下拉菜单的帧。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|[in]*bNotify*|未使用。|  
  
### <a name="remarks"></a>备注  
 创建时的下拉列表帧或调整父窗口大小时，框架将调用此方法。 此方法使用的位置和父窗口的大小计算的位置和大小的下拉菜单的帧。  
  
##  <a name="setautodestroy"></a>  CMFCDropDownFrame::SetAutoDestroy  
 设置是否自动销毁子下拉工具栏窗口。  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bAutoDestroy*  
 `TRUE` 自动销毁关联的下拉工具栏窗口中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果*bAutoDestroy*是`TRUE`，则`CMFCDropDownFrame`析构函数销毁关联的下拉工具栏窗口。 默认值为 `TRUE`。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
