---
title: CMFCBaseToolBar 类
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar::GetDockingMode
- AFXBASETOOLBAR/CMFCBaseToolBar::GetMinSize
- AFXBASETOOLBAR/CMFCBaseToolBar::OnAfterChangeParent
helpviewer_keywords:
- CMFCBaseToolBar [MFC], GetDockingMode
- CMFCBaseToolBar [MFC], GetMinSize
- CMFCBaseToolBar [MFC], OnAfterChangeParent
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
ms.openlocfilehash: 027fe8569ff133bb3f348c9d0607f19c6d778c4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367832"
---
# <a name="cmfcbasetoolbar-class"></a>CMFCBaseToolBar 类

工具栏的基类。

## <a name="syntax"></a>语法

```
class CMFCBaseToolBar : public CPane
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCBaseToolBar::CMFCBaseToolBar`|默认构造函数。|
|`CMFCBaseToolBar::~CMFCBaseToolBar`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CMFCBaseToolBar::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCBase工具栏：获取停靠模式](#getdockingmode)|返回停靠模式。 （覆盖[CBasePane：获取停靠模式](../../mfc/reference/cbasepane-class.md#getdockingmode)。|
|[CMFCBase工具栏：获取最小值](#getminsize)|返回工具栏的最小大小。 （覆盖[CPane：获取最小值](../../mfc/reference/cpane-class.md#getminsize)。|
|[CMFCBase工具栏：在更改后家长](#onafterchangeparent)|在窗格的父级更改后由框架调用。 （覆盖[CBasePane：之后更改父项](../../mfc/reference/cbasepane-class.md#onafterchangeparent)。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具栏](../../mfc/reference/cmfcbasetoolbar-class.md)

## <a name="requirements"></a>要求

**标题：** afxbasetoolbar.h

## <a name="cmfcbasetoolbargetdockingmode"></a><a name="getdockingmode"></a>CMFCBase工具栏：获取停靠模式

返回停靠模式。

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>返回值

停靠模式。

## <a name="cmfcbasetoolbargetminsize"></a><a name="getminsize"></a>CMFCBase工具栏：获取最小值

返回工具栏的最小大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>参数

*大小*<br/>
[出]工具栏的最小大小。

## <a name="cmfcbasetoolbaronafterchangeparent"></a><a name="onafterchangeparent"></a>CMFCBase工具栏：在更改后家长

在窗格的父级更改后由框架调用。

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>参数

*pWndOld 父级*<br/>
[在]指向上一个父窗口的指针。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
