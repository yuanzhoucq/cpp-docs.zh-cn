---
title: CGlobalUtils 类
ms.date: 10/18/2018
f1_keywords:
- CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils::AdjustRectToWorkArea
- AFXGLOBALUTILS/CGlobalUtils::CalcExpectedDockedRect
- AFXGLOBALUTILS/CGlobalUtils::CanBeAttached
- AFXGLOBALUTILS/CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd
- AFXGLOBALUTILS/CGlobalUtils::CheckAlignment
- AFXGLOBALUTILS/CGlobalUtils::CyFromString
- AFXGLOBALUTILS/CGlobalUtils::DecimalFromString
- AFXGLOBALUTILS/CGlobalUtils::FlipRect
- AFXGLOBALUTILS/CGlobalUtils::ForceAdjustLayout
- AFXGLOBALUTILS/CGlobalUtils::GetDockingManager
- AFXGLOBALUTILS/CGlobalUtils::GetOppositeAlignment
- AFXGLOBALUTILS/CGlobalUtils::GetPaneAndAlignFromPoint
- AFXGLOBALUTILS/CGlobalUtils::GetWndIcon
- AFXGLOBALUTILS/CGlobalUtils::SetNewParent
- AFXGLOBALUTILS/CGlobalUtils::StringFromCy
- AFXGLOBALUTILS/CGlobalUtils::StringFromDecimal
helpviewer_keywords:
- CGlobalUtils [MFC], AdjustRectToWorkArea
- CGlobalUtils [MFC], CalcExpectedDockedRect
- CGlobalUtils [MFC], CanBeAttached
- CGlobalUtils [MFC], CanPaneBeInFloatingMultiPaneFrameWnd
- CGlobalUtils [MFC], CheckAlignment
- CGlobalUtils [MFC], CyFromString
- CGlobalUtils [MFC], DecimalFromString
- CGlobalUtils [MFC], FlipRect
- CGlobalUtils [MFC], ForceAdjustLayout
- CGlobalUtils [MFC], GetDockingManager
- CGlobalUtils [MFC], GetOppositeAlignment
- CGlobalUtils [MFC], GetPaneAndAlignFromPoint
- CGlobalUtils [MFC], GetWndIcon
- CGlobalUtils [MFC], SetNewParent
- CGlobalUtils [MFC], StringFromCy
- CGlobalUtils [MFC], StringFromDecimal
ms.assetid: 2c5bd1a6-f80c-4e79-a476-b4ceebabfb2f
ms.openlocfilehash: 66c1663774076fcc4b62b766b1781efc8cc33c93
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373726"
---
# <a name="cglobalutils-class"></a>CGlobalUtils 类

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CGlobalUtils
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CGlobalUtils::AdjustRectToWorkArea](#adjustrecttoworkarea)||
|[CGlobalUtils::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CGlobalUtils::CanBeAttached](#canbeattached)||
|[CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd](#canpanebeinfloatingmultipaneframewnd)||
|[CGlobalUtils::CheckAlignment](#checkalignment)||
|[CGlobalUtils::CyFromString](#cyfromstring)||
|[CGlobalUtils::DecimalFromString](#decimalfromstring)||
|[CGlobalUtils::FlipRect](#fliprect)||
|[CGlobalUtils::ForceAdjustLayout](#forceadjustlayout)||
|[CGlobalUtils：：获取扩展管理器](#getdockingmanager)||
|[CGlobalUtils：获得相反对齐](#getoppositealignment)||
|[CGlobalUtils：：获取窗格和从点对齐](#getpaneandalignfrompoint)||
|[CGlobalUtils：获取WndIcon](#getwndicon)||
|[CGlobalUtils::SetNewParent](#setnewparent)||
|[CGlobalUtils::StringFromCy](#stringfromcy)||
|[CGlobalUtils::StringFromDecimal](#stringfromdecimal)||

## <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

[CGlobalUtils](../../mfc/reference/cglobalutils-class.md)

## <a name="requirements"></a>要求

**标题：** afxglobalutils.h

## <a name="cglobalutilsadjustrecttoworkarea"></a><a name="adjustrecttoworkarea"></a>CGlobalUtils：：调整RecttoWork区域

```
void AdjustRectToworkArea(
    CRect& rect,
    CRect* pRectDelta = NULL);
```

### <a name="parameters"></a>参数

[进出]*rect*<br/>
[在]*普雷克拉德尔塔*<br/>

### <a name="remarks"></a>备注

## <a name="cglobalutilscalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CGlobalUtils：：钙化物多克

```
void CalcExpectedDockedRect(
    CPaneContainerManager& barContainerManager,
    CWnd* pWndTodock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>参数

[在]*酒吧容器管理器*<br/>

[在]*普恩德托多克*<br/>

[在]*ptMouse*<br/>

[出]*rectResult*<br/>

[出]*bDrawTab*<br/>

[出]*ppTargetBar*<br/>

### <a name="remarks"></a>备注

## <a name="cglobalutilscanbeattached"></a><a name="canbeattached"></a>CGlobalUtils：：可附加

```
BOOL CanBeAttached(CWnd* pWnd) const;
```

### <a name="parameters"></a>参数

[在]*pwnd*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cglobalutilscanpanebeinfloatingmultipaneframewnd"></a><a name="canpanebeinfloatingmultipaneframewnd"></a>CGlobalUtils：：坎帕内贝在漂浮的多窗格框架

```
BOOL CanPaneBeInFloatingMultiPaneFrameWnd(CWnd* pWnd) const;
```

### <a name="parameters"></a>参数

[在]*pwnd*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cglobalutilscheckalignment"></a><a name="checkalignment"></a>CGlobalUtils：检查对齐

```
BOOL CheckAlignment(
    CPoint point,
    CBasePane* pBar,
    int nSensitivity,
    const CDockingManager* pDockManager,
    BOOL bOuterEdge,
    DWORD& dwAlignment,
    DWORD dwEnabledDockBars = CBRS_ALIGN_ANY,
    LPCRECT lpRectBounds = NULL) const;
```

### <a name="parameters"></a>参数

[在]*点*<br/>

[在]*pBar*<br/>

[在]*nSensitivity*<br/>

[在]*pDock管理器*<br/>

[在]*bouterEdge*<br/>

[出]*dwalignment*<br/>

[在]*dwEnabledDockBars*<br/>

[在]*lpRectBounds*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cglobalutilscyfromstring"></a><a name="cyfromstring"></a>CGlobalUtils：：CyFromString

```
BOOL CyFromString(
    CY& cy,
    LPCTSTR psz);
```

### <a name="parameters"></a>参数

[出]*cy*<br/>

[在]*psz*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cglobalutilsdecimalfromstring"></a><a name="decimalfromstring"></a>CGlobalUtils：:D从弦

```
BOOL DecimalFromString(
    DECIMAL& decimal,
    LPCTSTR psz);
```

### <a name="parameters"></a>参数

[出]*十进制*<br/>

[在]*psz*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cglobalutilsfliprect"></a><a name="fliprect"></a>CGlobalUtils：：翻转

```
void FlipRect(
    CRect& rect,
    int nDegrees);
```

### <a name="parameters"></a>参数

[进出]*rect*<br/>
[在]*n 度*<br/>

### <a name="remarks"></a>备注

## <a name="cglobalutilsforceadjustlayout"></a><a name="forceadjustlayout"></a>CGlobalUtils：：强制调整布局

```
void ForceAdjustLayout(
    CDockingManager* pDockManager,
    BOOL bForce = FALSE,
    BOOL bForceInvisible = FALSE);
```

### <a name="parameters"></a>参数

[进出]*pDock管理器*<br/>

[在]*bForce*<br/>

[在]*bForce 隐形*<br/>

### <a name="remarks"></a>备注

## <a name="cglobalutilsgetdockingmanager"></a><a name="getdockingmanager"></a>CGlobalUtils：：获取扩展管理器

```
CDockingManager* GetDockingManager(CWnd* pWnd);
```

### <a name="parameters"></a>参数

[在]*pwnd*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cglobalutilsgetoppositealignment"></a><a name="getoppositealignment"></a>CGlobalUtils：获得相反对齐

```
DWORD GetOppositeAlignment(DWORD dwAlign);
```

### <a name="parameters"></a>参数

[在]*dwalign*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cglobalutilsgetpaneandalignfrompoint"></a><a name="getpaneandalignfrompoint"></a>CGlobalUtils：：获取窗格和从点对齐

```
BOOL GetPaneAndAlignFromPoint(
    CPaneContainerManager& barContainerManager,
    CPoint pt,
    CDockablePane** ppTargetControlBar,
    DWORD& dwAlignment,
    BOOL& bTabArea,
    BOOL& bCaption);
```

### <a name="parameters"></a>参数

[在]*酒吧容器管理器*<br/>

[在]*pt*<br/>

[出]*ppTarget控制栏*<br/>

[出]*dwalignment*<br/>

[出]*bTabArea*<br/>

[出]*bCaption*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cglobalutilsgetwndicon"></a><a name="getwndicon"></a>CGlobalUtils：获取WndIcon

```
HICON GetWndIcon(CWnd* pWnd);
```

### <a name="parameters"></a>参数

[在]*pwnd*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cglobalutilssetnewparent"></a><a name="setnewparent"></a>CGlobalUtils：：设置新家长

```
void SetNewParent(
    CObList& lstControlBars,
    CWnd* pNewParent,
    BOOL bCheckVisibility = TRUE);
```

### <a name="parameters"></a>参数

[在]*lstControlBars*<br/>

[在]*p 新家长*<br/>

[在]*b 检查可见性*<br/>

### <a name="remarks"></a>备注

## <a name="cglobalutilsstringfromcy"></a><a name="stringfromcy"></a>CGlobalUtils：：弦从西

```
BOOL StringFromCy(
    CString& str,
    CY& cy);
```

### <a name="parameters"></a>参数

[出]*斯特*<br/>

[在]*cy*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cglobalutilsstringfromdecimal"></a><a name="stringfromdecimal"></a>CGlobalUtils：从十进制的字符串

```
BOOL StringFromDecimal(
    CString& str,
    DECIMAL& decimal);
```

### <a name="parameters"></a>参数

[出]*斯特*<br/>

[在]*十进制*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
