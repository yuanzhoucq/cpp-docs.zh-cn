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
ms.openlocfilehash: 0c2fed4aa239faa96abf692a46a27102ce9820a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403680"
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu 类

表示一个用户使用的文档或应用程序中选择颜色的弹出菜单。

## <a name="syntax"></a>语法

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|描述|
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|构造 `CMFCColorPopupMenu` 对象。|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|创建一个可停靠分开的颜色条。 (重写[CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar)。)|
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|返回[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)嵌入到弹出菜单。 (重写[CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar)。)|
|`CMFCColorPopupMenu::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|设置的属性网格控件对象嵌入的`CMFCColorBar`对象。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|名称|描述|
|`m_bEnabledInCustomizeMode`|一个布尔值，该值确定是否显示在颜色栏。|
|`m_wndColorBar`|`CMFCColorBar`提供颜色选择的对象。|

### <a name="remarks"></a>备注

此类继承的弹出菜单功能`CMFCPopupMenu`类，并管理`CMFCColorBar`提供颜色选择的对象。 当工具栏框架为自定义模式和`m_bEnabledInCustomizeMode`成员设置为 FALSE，将不显示颜色条对象。 有关自定义模式的详细信息，请参阅[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

有关详细信息`CMFCColorBar`，请参阅[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>要求

**标头：** afxcolorpopupmenu.h

##  <a name="cmfccolorpopupmenu"></a>  CMFCColorPopupMenu::CMFCColorPopupMenu

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

*colors*<br/>
[in]框架显示弹出菜单的颜色的数组。

*color*<br/>
[in]默认选择的颜色。

*lpszAutoColor*<br/>
[in]文本标签*自动*（默认值） 颜色按钮，则为 NULL。

标准标签为自动按钮**自动**。

*lpszOtherColor*<br/>
[in]文本标签*其他*按钮，其中显示更多颜色选项，则为 NULL。

其他按钮的标准标签**更多颜色...**.

*lpszDocColors*<br/>
[in]文档颜色按钮的文本标签。 文档颜色调色板，列出所有的文档当前使用的颜色。

*lstDocColors*<br/>
[in]文档当前使用的颜色的列表。

*nColumns*<br/>
[in]颜色数组具有的列数。

*nHorzDockRows*<br/>
[in]颜色栏中的水平停靠时的行数。

*nVertDockColumns*<br/>
[in]颜色栏中的垂直停靠时的列数。

*colorAutomatic*<br/>
[in]在框架应用单击自动按钮时的默认颜色。

*uiCommandID*<br/>
[in]颜色条控制命令 id。

*bStdColorDlg*<br/>
[in]一个布尔值，该值指示是否显示标准系统颜色对话框中或[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)对话框。

*pParentBtn*<br/>
[in]指向父按钮的指针。

*nID*<br/>
[in]命令 id。

### <a name="remarks"></a>备注

每个重载构造函数设置`m_bEnabledInCustomizeMode`成员为 FALSE。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCColorPopupMenu`对象。

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

##  <a name="createtearoffbar"></a>  CMFCColorPopupMenu::CreateTearOffBar

创建一个可停靠分开的颜色条。

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pWndMain*|[in]向父窗口的拖曳栏的指针。|
|*uiID*|[in]拖曳栏的命令 ID。|
|*lpszName*|[in]拖曳栏的窗口文本。|

### <a name="return-value"></a>返回值

指向新拖曳控件条对象的指针。

### <a name="remarks"></a>备注

此方法创建[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)对象并将其强制转换[CPane 类](../../mfc/reference/cpane-class.md)指针。 可以将此值强制转换回[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)指针使用中所述的强制转换宏之一[MFC 类对象的类型强制转换](../../mfc/reference/type-casting-of-mfc-class-objects.md)。

##  <a name="getmenubar"></a>  CMFCColorPopupMenu::GetMenuBar

返回[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)嵌入到弹出菜单。

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>返回值

指向嵌入的`CMFCPopupMenuBar`。

### <a name="remarks"></a>备注

颜色弹出菜单将包含嵌入式[CMFCPopupMenuBar 类](../../mfc/reference/cmfcpopupmenubar-class.md)对象。 如果应用程序使用不同的嵌入的类型重写此方法在派生类中。

##  <a name="setproplist"></a>  CMFCColorPopupMenu::SetPropList

设置的属性网格控件对象嵌入的`CMFCColorBar`对象。

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>参数

*pWndList*<br/>
[in]为属性网格控件对象的指针。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
