---
title: CDockablePaneAdapter 类
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
ms.openlocfilehash: 88c125c63f9dbfe272f5d543e996366575fc533b
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866220"
---
# <a name="cdockablepaneadapter-class"></a>CDockablePaneAdapter 类

为 `CWnd`派生窗格提供停靠支持。

## <a name="syntax"></a>语法

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|返回包装的窗口。|
|[CDockablePaneAdapter::LoadState](#loadstate)|(重写[CDockablePane:: LoadState](cdockablepane-class.md#loadstate)。)|
|[CDockablePaneAdapter::SaveState](#savestate)|(重写[CDockablePane:: SaveState](cdockablepane-class.md)。)|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>备注

通常, 当你使用[CMFCBaseTabCtrl:: AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)或[CMFCBaseTabCtrl:: InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab)方法时, 框架将实例化此类的对象。

如果要自定义`CDockablePaneAdapter`行为, 只需从其派生新类, 并通过使用[CMFCBaseTabCtrl:: SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc)将运行时类信息设置为选项卡式窗口。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CDockablePane](../../mfc/reference/cdockablepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>要求

**标头:** afxDockablePaneAdapter

##  <a name="getwrappedwnd"></a>CDockablePaneAdapter:: GetWrappedWnd

返回可停靠窗格适配器的基础窗口。

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>返回值

指向已包装窗口的指针。

### <a name="remarks"></a>备注

使用此函数可访问包装的窗口。

##  <a name="loadstate"></a>  CDockablePaneAdapter::LoadState

从注册表加载窗格的状态。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
中配置文件名称。

*nIndex*<br/>
中配置文件索引。

*uiID*<br/>
中窗格 ID。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="savestate"></a>CDockablePaneAdapter:: SaveState

将窗格状态保存到注册表。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
中配置文件名称。

*nIndex*<br/>
中配置文件索引 (默认为窗口的控件 ID)。

*uiID*<br/>
中窗格 ID。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="setwrappedwnd"></a>CDockablePaneAdapter:: SetWrappedWnd

为可停靠的窗格适配器设置基础窗口。

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中指向要包装的窗格适配器的窗口的指针。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)
