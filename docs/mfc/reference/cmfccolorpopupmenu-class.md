---
title: CMFCColorPopupMenu 类
ms.date: 11/04/2016
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
ms.openlocfilehash: bcdf60c974ecdc437b90891d2b46a5eec94859d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367682"
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu 类

表示用户用于选择文档或应用程序中颜色的弹出式菜单。

## <a name="syntax"></a>语法

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|[CMFC颜色弹出菜单：：CMFC颜色弹出菜单](#cmfccolorpopupmenu)|构造 `CMFCColorPopupMenu` 对象。|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFC颜色弹出菜单：：创建眼泪关闭栏](#createtearoffbar)|创建可停靠的撕掉颜色条。 （覆盖[CMFC 弹出菜单：：创建"创建"关闭栏](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar)"）|
|[CMFC颜色弹出菜单：：获取菜单栏](#getmenubar)|返回嵌入在弹出式菜单中的[CMFCPopupMenuBar。](../../mfc/reference/cmfcpopupmenubar-class.md) （覆盖[CMFC 弹出菜单：：获取菜单栏](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar)。|
|`CMFCColorPopupMenu::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFC颜色弹出菜单：：设置Proplist](#setproplist)|设置嵌入`CMFCColorBar`对象的属性网格控制对象。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|名称|说明|
|`m_bEnabledInCustomizeMode`|确定是否显示颜色条的布尔值。|
|`m_wndColorBar`|提供`CMFCColorBar`颜色选择的对象。|

### <a name="remarks"></a>备注

此类继承`CMFCPopupMenu`类的弹出菜单功能，并管理提供颜色选择`CMFCColorBar`的对象。 当工具栏框架处于自定义模式且`m_bEnabledInCustomizeMode`成员设置为 FALSE 时，不会显示颜色栏对象。 有关自定义模式的详细信息，请参阅[CMFCToolBar：：是自定义模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

有关 的详细信息`CMFCColorBar`，请参阅[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFC颜色弹出菜单](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>要求

**标题：** afxcolorpopmenu.h

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a>CMFC颜色弹出菜单：：CMFC颜色弹出菜单

构造 `CMFCColorPopupMenu` 对象。

```
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    int nHorzDockRows,
    int nVertDockColumns,
    COLORREF colorAutomatic,
    UINT uiCommandID,
    BOOL bStdColorDlg = FALSE);

CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic);

CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nID);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]框架显示在弹出式菜单上的颜色数组。

*颜色*<br/>
[在]默认选择的颜色。

*lpsz自动颜色*<br/>
[在]*自动*（默认）颜色按钮或 NULL 的文本标签。

自动按钮的标准标签是 **"自动**"。

*lpszOther颜色*<br/>
[在]*另*一个按钮的文本标签，显示更多颜色选项，或 NULL。

另一个按钮的标准标签是 **"更多颜色..."**

*lpszDocColors*<br/>
[在]文档颜色按钮的文本标签。 文档颜色调色板列出文档当前使用的所有颜色。

*lstDocColors*<br/>
[在]文档当前使用的颜色列表。

*nColumns*<br/>
[在]颜色数组的列数。

*n霍兹多克罗茨*<br/>
[在]颜色栏水平停靠时的行数。

*nVertDock 柱子*<br/>
[在]颜色栏垂直停靠时的列数。

*颜色 自动*<br/>
[在]单击自动按钮时框架适用的默认颜色。

*uiCommandID*<br/>
[在]颜色条控制命令 ID。

*bStdColorDlg*<br/>
[在]指示是显示标准系统颜色对话框还是[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)对话框的布尔。

*p 家长Btn*<br/>
[在]指向父按钮的指针。

*nID*<br/>
[在]命令 ID。

### <a name="remarks"></a>备注

每个重载构造函数将`m_bEnabledInCustomizeMode`成员设置为 FALSE。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCColorPopupMenu`对象。

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a>CMFC颜色弹出菜单：：创建眼泪关闭栏

创建可停靠的撕掉颜色条。

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*普恩德·梅因*|[在]指向撕开条的父窗口。|
|*uiID*|[在]撕开栏的命令 ID。|
|*lpsz名称*|[在]撕开栏的窗口文本。|

### <a name="return-value"></a>返回值

指向新撕掉控制栏对象的指针。

### <a name="remarks"></a>备注

此方法创建一个[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)对象，并将其转换为[CPane 类](../../mfc/reference/cpane-class.md)指针。 您可以使用[MFC 类对象的类型转换](../../mfc/reference/type-casting-of-mfc-class-objects.md)中描述的强制转换宏之一将此值转换回[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)指针。

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a>CMFC颜色弹出菜单：：获取菜单栏

返回嵌入在弹出式菜单中的[CMFCPopupMenuBar。](../../mfc/reference/cmfcpopupmenubar-class.md)

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>返回值

指向嵌入`CMFCPopupMenuBar`的 指针。

### <a name="remarks"></a>备注

颜色弹出式菜单具有嵌入[的 CMFCPopupMenuBar 类](../../mfc/reference/cmfcpopupmenubar-class.md)对象。 如果应用程序使用不同的嵌入类型，则在派生类中重写此方法。

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a>CMFC颜色弹出菜单：：设置Proplist

设置嵌入`CMFCColorBar`对象的属性网格控制对象。

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>参数

*pwndlist*<br/>
[在]指向属性网格控件对象的指针。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
