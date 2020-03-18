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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425831"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame 类

向下拉工具栏和下拉工具栏按钮提供下拉框架窗口功能。

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
|名称|说明|
|[CMFCDropDownFrame：： Create](#create)|创建一个 `CMFCDropDownFrame` 对象。|
|`CMFCDropDownFrame::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|检索下拉框的父菜单栏。|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|检索下拉框的父弹出菜单。|
|`CMFCDropDownFrame::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCDropDownFrame：： RecalcLayout](#recalclayout)|重新定位下拉框。|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|设置子下拉工具栏窗口是否自动销毁。|

### <a name="remarks"></a>备注

此类不适于在您的代码中直接使用。

框架使用此类为 `CMFCDropDownToolbar` 和 `CMFCDropDownToolbarButton` 类提供框架行为。 有关这些类的详细信息，请参阅[CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)和[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)。

## <a name="example"></a>示例

下面的示例演示如何从 `CFrameWnd` 类检索指向 `CMFCDropDownFrame` 对象的指针，以及如何将子下拉工具栏窗口设置为自动销毁。

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

##  <a name="create"></a>CMFCDropDownFrame：： Create

创建一个 `CMFCDropDownFrame` 对象。

```
virtual BOOL Create(
    CWnd* pWndParent,
    int x,
    int y,
    CMFCDropDownToolBar* pWndOriginToolbar);
```

### <a name="parameters"></a>parameters

|||
|-|-|
|参数|说明|
|*pWndParent*|中下拉框的父窗口。|
|*x*|中下边框位置的水平屏幕坐标。|
|*y*|中下边框位置的垂直屏幕坐标。|
|*pWndOriginToolbar*|中具有此方法用来填充新下拉框架对象的下拉按钮的工具栏。|

### <a name="return-value"></a>返回值

如果已成功创建下拉框架，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法调用基本[CMiniFrameWnd：： CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法来创建具有 WS_POPUP 样式的下拉框窗口。 下拉框架窗口将出现在指定的屏幕坐标中。 如果[CMiniFrameWnd：： CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法返回 FALSE，则此方法将失败。

`CMFCDropDownFrame` 类创建所提供 `CMFCDropDownToolBar` 参数的副本。 此方法将按钮图像和按钮状态从 `pWndOriginToolbar` 参数复制到 `m_pWndOriginToolbar` 数据成员。

##  <a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar

检索下拉框的父菜单栏。

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>返回值

指向下拉框的父菜单栏的指针; 如果该框架没有父项，则为 NULL。

### <a name="remarks"></a>备注

此方法从父按钮检索父菜单栏。 如果下拉框没有父按钮或父按钮没有父菜单栏，则此方法返回 NULL。

##  <a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu

检索下拉框的父弹出菜单。

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>返回值

指向下拉框的父下拉菜单的指针，如果该框架没有父项，则为 NULL。

### <a name="remarks"></a>备注

此方法从父按钮检索父菜单。 如果下拉框没有父按钮或父按钮没有父菜单，则此方法返回 NULL。

##  <a name="recalclayout"></a>CMFCDropDownFrame：： RecalcLayout

重新定位下拉框。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>parameters

|||
|-|-|
|参数|说明|
|*bNotify*|中用.|

### <a name="remarks"></a>备注

创建下拉框架或调整父窗口大小时，框架将调用此方法。 此方法使用父窗口的位置和大小来计算下拉框的位置和大小。

##  <a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy

设置子下拉工具栏窗口是否自动销毁。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>parameters

*bAutoDestroy*<br/>
中若要自动销毁关联的下拉工具栏窗口，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果*bAutoDestroy*为 TRUE，则 `CMFCDropDownFrame` 析构函数会销毁关联的下拉工具栏窗口。 默认值为 TRUE。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
