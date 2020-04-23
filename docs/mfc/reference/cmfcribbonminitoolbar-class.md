---
title: CMFC功能迷你工具栏类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
ms.openlocfilehash: 5e5ac6c923640b7584d89a9c6f75d941deadddf3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754078"
---
# <a name="cmfcribbonminitoolbar-class"></a>CMFC功能迷你工具栏类

实现上下文快捷工具栏。

## <a name="syntax"></a>语法

```
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|默认构造函数。|
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCRibbonMiniToolBar::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|（重写 `CMFCPopupMenu::IsRibbonMiniToolBar`。）|
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|设置要在工具栏上显示的命令的列表。|
|[CMFCRibbonMiniToolBar::Show](#show)|在指定的屏幕坐标上显示浮动工具栏。|
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|显示浮动工具栏以及上下文菜单。|

## <a name="remarks"></a>备注

通常于用户在文档中选择对象后显示浮动工具栏。 例如，用户在文字处理程序中选择文本块后，应用程序将显示包含文本格式设置命令的浮动工具栏。

鼠标指针位于浮动工具栏边界之外时，浮动工具栏将变透明。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

`CMFCRibbonPanelMenu`

[CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)

## <a name="requirements"></a>要求

**标题：** afxRibbonMiniToolBar.h

## <a name="cmfcribbonminitoolbarsetcommands"></a><a name="setcommands"></a>CMFC 功能迷你工具栏：设置命令

设置要在工具栏上显示的命令的列表。

```cpp
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>参数

*pRibbonbar*<br/>
[在]迷你工具栏搜索要显示的按钮的功能区栏。

*lstCommands*<br/>
[在]要显示在迷你工具栏上的命令列表。 将搜索所有功能区类别以查找关联的按钮。

### <a name="remarks"></a>备注

使用此函数可以设置要显示在迷你工具栏中的命令列表。

### <a name="example"></a>示例

下面的示例演示如何使用`SetCommands``CMFCRibbonMiniToolBar`类的方法。 此代码段是 MS [Office 2007 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

## <a name="cmfcribbonminitoolbarshow"></a><a name="show"></a>CMFC功能迷你工具栏：显示

在指定的屏幕坐标上显示浮动工具栏。

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>参数

*x*<br/>
[在]在屏幕坐标中指定迷你工具栏的水平位置。

*Y*<br/>
[在]在屏幕坐标中指定迷你工具栏的垂直位置。

### <a name="return-value"></a>返回值

如果迷你工具栏已成功显示，则为 TRUE;否则，FALSE。

## <a name="cmfcribbonminitoolbarshowwithcontextmenu"></a><a name="showwithcontextmenu"></a>CMFC 功能迷你工具栏：：显示与上下文菜单

显示浮动工具栏以及上下文菜单。

```
BOOL ShowWithContextMenu(
    int x,
    int y,
    UINT uiMenuResID,
    CWnd* pWndOwner);
```

### <a name="parameters"></a>参数

*x*<br/>
[在]指定屏幕坐标中上下文菜单的水平位置。

*Y*<br/>
[在]指定屏幕坐标中上下文菜单的垂直位置。

*uiMenuResID*<br/>
[在]指定要显示的上下文菜单的资源 ID。

*pwndOwner*<br/>
[在]标识从上下文菜单接收消息的窗口。

### <a name="return-value"></a>返回值

如果上下文菜单成功显示，则为 TRUE;如果上下文菜单已成功显示，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

使用此功能可显示具有上下文菜单的迷你工具栏。 上下文菜单位于迷你工具栏下方 15 像素。

## <a name="cmfcribbonminitoolbariscontextmenumode"></a><a name="iscontextmenumode"></a>CMFC功能放大缩小字体功能 放大缩小字体功能

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonminitoolbarisribbonminitoolbar"></a><a name="isribbonminitoolbar"></a>CMFC 功能迷你工具栏：是带状迷你工具栏

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
