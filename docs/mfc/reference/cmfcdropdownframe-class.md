---
title: CMFCDropDownFrame 类
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
ms.openlocfilehash: 534dc90443371c8440e0cb317540f2cf80f6eacc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284744"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame 类

提供下拉工具栏和下拉工具栏按钮的下拉列表框架窗口的功能。

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
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|检索父菜单栏的下拉列表框。|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|检索父弹出菜单的下拉列表框。|
|`CMFCDropDownFrame::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|重新定位的下拉列表帧。|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|设置是否自动销毁子下拉工具栏窗口。|

### <a name="remarks"></a>备注

此类不适于在代码中直接使用。

框架将使用此类提供帧行为`CMFCDropDownToolbar`和`CMFCDropDownToolbarButton`类。 有关这些类的详细信息，请参阅[CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)并[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)。

## <a name="example"></a>示例

下面的示例演示如何检索一个指向`CMFCDropDownFrame`对象从`CFrameWnd`类，以及如何设置子下拉工具栏窗口自动销毁。

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
|*pWndParent*|[in]父窗口的下拉列表框。|
|*x*|[in]向下取帧的位置的水平屏幕坐标。|
|*y*|[in]向下取帧的位置垂直屏幕坐标。|
|*pWndOriginToolbar*|[in]具有此方法用于填充新的下拉列表帧对象下拉列表按钮工具栏。|

### <a name="return-value"></a>返回值

如果下拉列表帧已成功创建; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法调用了基[CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法创建具有 WS_POPUP 样式的下拉列表框架窗口。 下拉列表框架窗口将显示在指定的屏幕坐标。 如果此方法将失败[CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法返回 FALSE。

`CMFCDropDownFrame`类创建一份提供的`CMFCDropDownToolBar`参数。 此方法会复制按钮图像和按钮状态从`pWndOriginToolbar`参数`m_pWndOriginToolbar`数据成员。

##  <a name="getparentmenubar"></a>  CMFCDropDownFrame::GetParentMenuBar

检索父菜单栏的下拉列表框。

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>返回值

一个指向父菜单栏的下拉列表帧或如果帧已没有父级，则为 NULL。

### <a name="remarks"></a>备注

此方法检索从父按钮的父菜单栏。 如果下拉列表框没有父按钮或父按钮具有任何父菜单栏，此方法将返回 NULL。

##  <a name="getparentpopupmenu"></a>  CMFCDropDownFrame::GetParentPopupMenu

检索父弹出菜单的下拉列表框。

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>返回值

一个指向父下拉列表菜单的下拉列表帧或如果帧已没有父级，则为 NULL。

### <a name="remarks"></a>备注

此方法检索从父按钮的父菜单。 如果下拉列表框没有父按钮或父按钮具有任何父菜单，此方法将返回 NULL。

##  <a name="recalclayout"></a>  CMFCDropDownFrame::RecalcLayout

重新定位的下拉列表帧。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*bNotify*|[in]未使用。|

### <a name="remarks"></a>备注

创建下拉列表框或调整父窗口时，框架将调用此方法。 此方法使用的位置和父窗口的大小计算的位置和下拉列表帧的大小。

##  <a name="setautodestroy"></a>  CMFCDropDownFrame::SetAutoDestroy

设置是否自动销毁子下拉工具栏窗口。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*bAutoDestroy*<br/>
[in]为 TRUE，则自动销毁关联的下拉列表工具栏窗口中;否则为 FALSE。

### <a name="remarks"></a>备注

如果*bAutoDestroy*为 TRUE，则`CMFCDropDownFrame`析构函数销毁关联的下拉工具栏窗口。 默认值为 TRUE。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
