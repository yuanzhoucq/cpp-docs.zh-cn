---
title: CSsDockSiteInfo 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 9f23d5aff2bac65363086c077af45e35c3263f65
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750566"
---
# <a name="crecentdocksiteinfo-class"></a>CSsDockSiteInfo 类

该`CRecentDockSiteInfo`类是一个帮助类，用于存储[CPane 类](../../mfc/reference/cpane-class.md)的最近状态信息。

## <a name="syntax"></a>语法

```
class CRecentDockSiteInfo : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CRecentDockSiteInfo::CRecentDockSiteInfo`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CRecentDockSiteInfo::CleanUp](#cleanup)||
|[CSsDock 网站信息：：获取最新默认窗格分隔器](#getrecentdefaultpanedivider)||
|[CSsDockSite信息：：获取最新停靠百分比](#getrecentdockedpercent)||
|[CSsDockSite信息：：获取最新多克](#getrecentdockedrect)||
|[CSsdock 网站信息：：获取最新列表的窗格](#getrecentlistofpanes)||
|[CSsDockSite信息：：获取最新窗格容器](#getrecentpanecontainer)||
|[CSsdockSite信息：：获取最新选项卡容器](#getrecenttabcontainer)||
|[CRecentDockSiteInfo::Init](#init)||
|[CRecentDockSiteInfo::IsRecentLeftPane](#isrecentleftpane)||
|[CSsDockSite信息：：操作员 |](#operator_eq)||
|[CRecentDockSiteInfo::SaveListOfRecentPanes](#savelistofrecentpanes)||
|[CRecentDockSiteInfo::SetInfo](#setinfo)||
|[CRecentDockSiteInfo::StoreDockInfo](#storedockinfo)||

## <a name="remarks"></a>备注

`CRecentDockSiteInfo` 类是数据管理类。 它在 `CPane` 在停靠与浮动之间转换时跟踪其最近状态。 当用户双击浮动的可停靠窗格时，它会成为停靠状态。 双击停靠的窗格会使它恢复为以前的位置、大小和状态。 同样，当窗格重新停靠时，它会返回到以前的停靠位置。 通过此数据类可以实现此行为。 由于此类的成员存储停靠的窗格的状态信息，因此它们不应由应用程序直接修改。

每次创建窗格时会创建一个 `CRecentDockSiteInfo` 对象。 每个`CPane`对象都有一个成员变量[CPane：m_recentDockInfo，](../../mfc/reference/cpane-class.md#m_recentdockinfo)用于存储此信息。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md)

## <a name="requirements"></a>要求

**标题：** afxssdockSiteInfo.h

## <a name="crecentdocksiteinfocleanup"></a><a name="cleanup"></a>CSsdock网站信息：：清理

```cpp
void CleanUp();
```

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfocrecentdocksiteinfo"></a><a name="crecentdocksiteinfo"></a>CSsDock网站信息：：C_ssdock网站信息

```
CRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>参数

[在]*pBar*<br/>

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfogetrecentdefaultpanedivider"></a><a name="getrecentdefaultpanedivider"></a>CSsDock 网站信息：：获取最新默认窗格分隔器

```
CPaneDivider* GetRecentDefaultPaneDivider();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfogetrecentdockedpercent"></a><a name="getrecentdockedpercent"></a>CSsDockSite信息：：获取最新停靠百分比

```
int GetRecentDockedPercent(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[在]*bForSlider*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfogetrecentdockedrect"></a><a name="getrecentdockedrect"></a>CSsDockSite信息：：获取最新多克

```
CRect& GetRecentDockedRect(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[在]*bForSlider*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfogetrecentlistofpanes"></a><a name="getrecentlistofpanes"></a>CSsdock 网站信息：：获取最新列表的窗格

```
CList<HWND, HWND>& GetRecentListOfPanes(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[在]*bForSlider*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfogetrecentpanecontainer"></a><a name="getrecentpanecontainer"></a>CSsDockSite信息：：获取最新窗格容器

```
CPaneContainer* GetRecentPaneContainer(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[在]*bForSlider*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfogetrecenttabcontainer"></a><a name="getrecenttabcontainer"></a>CSsdockSite信息：：获取最新选项卡容器

```
CPaneContainer* GetRecentTabContainer(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[在]*bForSlider*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfoinit"></a><a name="init"></a>CSinDockSite信息：：Init

```cpp
void Init();
```

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfoisrecentleftpane"></a><a name="isrecentleftpane"></a>CSsdocksite信息：：最近左窗格

```
BOOL IsRecentLeftPane(BOOL bForSlider);
```

### <a name="parameters"></a>参数

[在]*bForSlider*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfooperator-"></a><a name="operator_eq"></a>CSsDockSite信息：：操作员 |

```
CRecentDockSiteInfo& operator=(CRecentDockSiteInfo& src);
```

### <a name="parameters"></a>参数

[在]*斯尔克*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfosavelistofrecentpanes"></a><a name="savelistofrecentpanes"></a>CS.DockSite信息：：保存最近窗格列表

```cpp
void SaveListOfRecentPanes(CList<HWND,
    HWND>& lstOrg,
    BOOL bForSlider);
```

### <a name="parameters"></a>参数

[在]*CList<HWND*<br/>
[在]*lstOrg*<br/>
[在]*bForSlider*<br/>

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfosetinfo"></a><a name="setinfo"></a>CSsDock网站信息：：SetInfo

```
virtual void SetInfo(
    BOOL bForSlider,
    CRecentDockSiteInfo& srcInfo);
```

### <a name="parameters"></a>参数

[在]*bForSlider*<br/>
[在]*srcInfo*<br/>

### <a name="remarks"></a>备注

## <a name="crecentdocksiteinfostoredockinfo"></a><a name="storedockinfo"></a>CSsDock网站信息：：商店多克信息

```
virtual void StoreDockInfo(
    CPaneContainer* pRecentContainer,
    CDockablePane* pTabbedBar = NULL);
```

### <a name="parameters"></a>参数

[在]*p最新容器*<br/>
[在]*pTabbedBar*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite Class](../../mfc/reference/cdocksite-class.md)
