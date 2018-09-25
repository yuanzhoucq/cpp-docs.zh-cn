---
title: CRecentDockSiteInfo 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRecentDockSiteInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::CleanUp
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDefaultPaneDivider
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDockedPercent
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentDockedRect
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentListOfPanes
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentPaneContainer
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::GetRecentTabContainer
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::Init
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::IsRecentLeftPane
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::SaveListOfRecentPanes
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::SetInfo
- AFXRECENTDOCKSITEINFO/CRecentDockSiteInfo::StoreDockInfo
dev_langs:
- C++
helpviewer_keywords:
- CRecentDockSiteInfo [MFC], CleanUp
- CRecentDockSiteInfo [MFC], GetRecentDefaultPaneDivider
- CRecentDockSiteInfo [MFC], GetRecentDockedPercent
- CRecentDockSiteInfo [MFC], GetRecentDockedRect
- CRecentDockSiteInfo [MFC], GetRecentListOfPanes
- CRecentDockSiteInfo [MFC], GetRecentPaneContainer
- CRecentDockSiteInfo [MFC], GetRecentTabContainer
- CRecentDockSiteInfo [MFC], Init
- CRecentDockSiteInfo [MFC], IsRecentLeftPane
- CRecentDockSiteInfo [MFC], SaveListOfRecentPanes
- CRecentDockSiteInfo [MFC], SetInfo
- CRecentDockSiteInfo [MFC], StoreDockInfo
ms.assetid: 2dd14f95-d5a2-4461-a7a5-2c6c36a3a165
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a949a487f04a0aaac1ddf6eb3597dc6243cea548
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403067"
---
# <a name="crecentdocksiteinfo-class"></a>CRecentDockSiteInfo 类

`CRecentDockSiteInfo`类是存储最近状态信息的帮助器类[CPane 类](../../mfc/reference/cpane-class.md)。

## <a name="syntax"></a>语法

```
class CRecentDockSiteInfo : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CRecentDockSiteInfo::CRecentDockSiteInfo`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRecentDockSiteInfo::CleanUp](#cleanup)||
|[CRecentDockSiteInfo::GetRecentDefaultPaneDivider](#getrecentdefaultpanedivider)||
|[CRecentDockSiteInfo::GetRecentDockedPercent](#getrecentdockedpercent)||
|[CRecentDockSiteInfo::GetRecentDockedRect](#getrecentdockedrect)||
|[CRecentDockSiteInfo::GetRecentListOfPanes](#getrecentlistofpanes)||
|[CRecentDockSiteInfo::GetRecentPaneContainer](#getrecentpanecontainer)||
|[CRecentDockSiteInfo::GetRecentTabContainer](#getrecenttabcontainer)||
|[CRecentDockSiteInfo::Init](#init)||
|[CRecentDockSiteInfo::IsRecentLeftPane](#isrecentleftpane)||
|[CRecentDockSiteInfo::operator =](#operator_eq)||
|[CRecentDockSiteInfo::SaveListOfRecentPanes](#savelistofrecentpanes)||
|[CRecentDockSiteInfo::SetInfo](#setinfo)||
|[CRecentDockSiteInfo::StoreDockInfo](#storedockinfo)||

## <a name="remarks"></a>备注

`CRecentDockSiteInfo` 类是数据管理类。 它在 `CPane` 在停靠与浮动之间转换时跟踪其最近状态。 当用户双击浮动的可停靠窗格时，它会成为停靠状态。 双击停靠的窗格会使它恢复为以前的位置、大小和状态。 同样，当窗格重新停靠时，它会返回到以前的停靠位置。 通过此数据类可以实现此行为。 由于此类的成员存储停靠的窗格的状态信息，因此它们不应由应用程序直接修改。

每次创建窗格时会创建一个 `CRecentDockSiteInfo` 对象。 每个`CPane`对象具有一个成员变量[cpane:: M_recentdockinfo](../../mfc/reference/cpane-class.md#m_recentdockinfo)，用于存储此信息。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md)

## <a name="requirements"></a>要求

**标头：** afxrecentDockSiteInfo.h

##  <a name="cleanup"></a>  CRecentDockSiteInfo::CleanUp


```
void CleanUp();
```

### <a name="remarks"></a>备注

##  <a name="crecentdocksiteinfo"></a>  CRecentDockSiteInfo::CRecentDockSiteInfo


```
CRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>参数

[in]*pBar*

### <a name="remarks"></a>备注

##  <a name="getrecentdefaultpanedivider"></a>  CRecentDockSiteInfo::GetRecentDefaultPaneDivider


```
CPaneDivider* GetRecentDefaultPaneDivider();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getrecentdockedpercent"></a>  CRecentDockSiteInfo::GetRecentDockedPercent


```
int GetRecentDockedPercent(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[in]*bForSlider*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getrecentdockedrect"></a>  CRecentDockSiteInfo::GetRecentDockedRect


```
CRect& GetRecentDockedRect(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[in]*bForSlider*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getrecentlistofpanes"></a>  CRecentDockSiteInfo::GetRecentListOfPanes


```
CList<HWND, HWND>& GetRecentListOfPanes(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[in]*bForSlider*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getrecentpanecontainer"></a>  CRecentDockSiteInfo::GetRecentPaneContainer


```
CPaneContainer* GetRecentPaneContainer(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[in]*bForSlider*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getrecenttabcontainer"></a>  CRecentDockSiteInfo::GetRecentTabContainer


```
CPaneContainer* GetRecentTabContainer(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[in]*bForSlider*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="init"></a>  CRecentDockSiteInfo::Init


```
void Init();
```

### <a name="remarks"></a>备注

##  <a name="isrecentleftpane"></a>  CRecentDockSiteInfo::IsRecentLeftPane


```
BOOL IsRecentLeftPane(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[in]*bForSlider*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="operator_eq"></a>  CRecentDockSiteInfo::operator =


```
CRecentDockSiteInfo& operator=(CRecentDockSiteInfo& src);
```

### <a name="parameters"></a>参数

[in]*src*

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="savelistofrecentpanes"></a>  CRecentDockSiteInfo::SaveListOfRecentPanes


```
void SaveListOfRecentPanes(CList<HWND,
    HWND>& lstOrg,
    BOOL bForSlider);
```

### <a name="parameters"></a>参数

*CList < HWND*<br/>
[in][in]*lstOrg* [in] *bForSlider*

### <a name="remarks"></a>备注

##  <a name="setinfo"></a>  CRecentDockSiteInfo::SetInfo


```
virtual void SetInfo(
    BOOL bForSlider,
    CRecentDockSiteInfo& srcInfo);
```

### <a name="parameters"></a>参数

*bForSlider*<br/>
[in][in]*srcInfo*

### <a name="remarks"></a>备注

##  <a name="storedockinfo"></a>  CRecentDockSiteInfo::StoreDockInfo


```
virtual void StoreDockInfo(
    CPaneContainer* pRecentContainer,
    CDockablePane* pTabbedBar = NULL);
```

### <a name="parameters"></a>参数

*pRecentContainer*<br/>
[in][in]*pTabbedBar*

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite 类](../../mfc/reference/cdocksite-class.md)
