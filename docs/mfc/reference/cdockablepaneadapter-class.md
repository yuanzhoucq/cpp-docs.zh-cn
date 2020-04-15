---
title: 可装窗格适配器类
ms.date: 11/04/2016
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
ms.openlocfilehash: 2fbaf99e4cc9bcbecf1a94012713b34e986f7ecb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375597"
---
# <a name="cdockablepaneadapter-class"></a>可装窗格适配器类

为 `CWnd`派生窗格提供停靠支持。

## <a name="syntax"></a>语法

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[可停靠的窗格适配器：：获取包装](#getwrappedwnd)|返回包装的窗口。|
|[CDockablePaneAdapter::LoadState](#loadstate)|（覆盖[可停靠窗格：：加载状态](cdockablepane-class.md#loadstate)。）|
|[CDockablePaneAdapter::SaveState](#savestate)|（覆盖[可停靠窗格：：保存状态](cdockablepane-class.md)。）|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>备注

通常，当您使用[CMFCBaseTabCtrl：：addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)或[CMFCBaseTabCtrl：：插入选项卡](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab)方法时，框架会实例化此类的对象。

如果要自定义`CDockablePaneAdapter`行为，只需从该类派生一个新类，并使用 CMFCBaseTabCtrl 将运行时类信息设置为选项卡式窗口[：：设置 DockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMD目标](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[Cwnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[可装板](../../mfc/reference/cdockablepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[可装板式窗格适配器](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>要求

**标题：** afxDock 可窗格适配器.h

## <a name="cdockablepaneadaptergetwrappedwnd"></a><a name="getwrappedwnd"></a>可停靠的窗格适配器：：获取包装

返回可停靠窗格适配器的基础窗口。

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>返回值

指向包装窗口的指针。

### <a name="remarks"></a>备注

使用此函数可以访问包装窗口。

## <a name="cdockablepaneadapterloadstate"></a><a name="loadstate"></a>可停靠窗格适配器：：加载状态

从注册表加载窗格的状态。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]配置文件名称。

*nIndex*<br/>
[在]配置文件索引。

*uiID*<br/>
[在]窗格 ID。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockablepaneadaptersavestate"></a><a name="savestate"></a>可停靠窗格适配器：：保存状态

将窗格的状态保存到注册表。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]配置文件名称。

*nIndex*<br/>
[在]配置文件索引（默认为窗口的控制 ID）。

*uiID*<br/>
[在]窗格 ID。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdockablepaneadaptersetwrappedwnd"></a><a name="setwrappedwnd"></a>可停靠窗格适配器：：套包

设置可停靠窗格适配器的基础窗口。

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]指向窗口的指针，用于窗格适配器换行。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
