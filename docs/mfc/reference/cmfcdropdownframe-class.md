---
title: CMFC下线框架类
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
ms.openlocfilehash: a5e95efe1880f1177490d55988ca1fe42c606b15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367544"
---
# <a name="cmfcdropdownframe-class"></a>CMFC下线框架类

为下拉工具栏和下拉工具栏按钮提供下拉框架窗口功能。

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
|[CMFC下线框架：创建](#create)|创建一个 `CMFCDropDownFrame` 对象。|
|`CMFCDropDownFrame::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFC下拉框架：获取父菜单栏](#getparentmenubar)|检索下拉框架的父菜单栏。|
|[CMFC下线框架：获取家长弹出菜单](#getparentpopupmenu)|检索下拉框架的父弹出式菜单。|
|`CMFCDropDownFrame::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFC向下帧：Recalclayout](#recalclayout)|重新定位下拉框架。|
|[CMFC下拉帧：：设置自动销毁](#setautodestroy)|设置子下拉工具栏窗口是否自动销毁。|

### <a name="remarks"></a>备注

此类不适于在您的代码中直接使用。

框架使用此类向 和`CMFCDropDownToolbar``CMFCDropDownToolbarButton`类提供帧行为。 有关这些类的详细信息，请参阅[CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)和[CMFCDropDown 下拉工具栏按钮类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)。

## <a name="example"></a>示例

下面的示例演示如何从`CMFCDropDownFrame``CFrameWnd`类检索指向对象的指针，以及如何将子下拉工具栏窗口设置为自动销毁。

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFC下线框架](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>要求

**标头：** afxdropdowntoolbar.h

## <a name="cmfcdropdownframecreate"></a><a name="create"></a>CMFC下线框架：创建

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
|*pwnd 父级*|[在]下拉框架的父窗口。|
|** x |[在]下下帧位置的水平屏幕坐标。|
|*Y*|[在]向下帧位置的垂直屏幕坐标。|
|*pWndOrigin工具栏*|[在]具有此方法用于填充新下拉框架对象的下拉按钮的工具栏。|

### <a name="return-value"></a>返回值

如果成功创建了下拉框架，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

此方法调用基本[CMiniFrameWnd：createEx](../../mfc/reference/cminiframewnd-class.md#createex)方法，以创建具有WS_POPUP样式的下拉框架窗口。 下拉框架窗口显示在指定的屏幕坐标处。 如果[CMiniFrameWnd：createEx](../../mfc/reference/cminiframewnd-class.md#createex)方法返回 FALSE，则此方法将失败。

类`CMFCDropDownFrame`创建提供的`CMFCDropDownToolBar`参数的副本。 此方法将按钮图像和按钮状态从`pWndOriginToolbar`参数复制到`m_pWndOriginToolbar`数据成员。

## <a name="cmfcdropdownframegetparentmenubar"></a><a name="getparentmenubar"></a>CMFC下拉框架：获取父菜单栏

检索下拉框架的父菜单栏。

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>返回值

指向下拉框架的父菜单栏的指针，如果框架没有父菜单，则指向 NULL。

### <a name="remarks"></a>备注

此方法从父按钮检索父菜单栏。 如果下拉框架没有父按钮或父按钮没有父菜单栏，则此方法返回 NULL。

## <a name="cmfcdropdownframegetparentpopupmenu"></a><a name="getparentpopupmenu"></a>CMFC下线框架：获取家长弹出菜单

检索下拉框架的父弹出式菜单。

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>返回值

指向下拉框架的父下拉菜单的指针，如果框架没有父级，则指向 NULL。

### <a name="remarks"></a>备注

此方法从父按钮检索父菜单。 如果下拉框架没有父按钮或父按钮没有父菜单，则此方法将返回 NULL。

## <a name="cmfcdropdownframerecalclayout"></a><a name="recalclayout"></a>CMFC向下帧：Recalclayout

重新定位下拉框架。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*b 通知*|[在]闲置。|

### <a name="remarks"></a>备注

创建下拉框架或调整父窗口大小时，框架将调用此方法。 此方法使用父窗口的位置和大小计算下拉框架的位置和大小。

## <a name="cmfcdropdownframesetautodestroy"></a><a name="setautodestroy"></a>CMFC下拉帧：：设置自动销毁

设置子下拉工具栏窗口是否自动销毁。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*bAuto销毁*<br/>
[在]TRUE 自动销毁关联的下拉工具栏窗口;否则，FALSE。

### <a name="remarks"></a>备注

如果*bAuto销毁*为 TRUE，`CMFCDropDownFrame`则析构函数将销毁关联的下拉工具栏窗口。 默认值为 TRUE。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC下拉工具栏类](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
