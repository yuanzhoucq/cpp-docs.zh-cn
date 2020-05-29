---
title: CMFC下拉工具栏类
ms.date: 11/19/2018
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
ms.openlocfilehash: 68dd976471b39d7f50c2f0378b2fce99ad3feeca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367601"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFC下拉工具栏类

当用户按住顶层工具栏按钮时显示的工具栏。

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC向下工具栏：：允许显示帕内菜单](#allowshowonpanemenu)|（重写 `CPane::AllowShowOnPaneMenu`。）|
|[CMFC下拉工具栏：：加载位图](#loadbitmap)|（覆盖[CMFC 工具栏：：加载位图](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).）|
|[CMFC下拉工具栏：：加载工具栏](#loadtoolbar)|（覆盖[CMFC 工具栏：LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).）|
|[CMFC下拉工具栏：：在LButtonup上](#onlbuttonup)||
|[CMFC向下工具栏：：鼠标移动](#onmousemove)||
|[CMFC下拉工具栏：打开发送命令](#onsendcommand)|（重写 `CMFCToolBar::OnSendCommand`。）|
|[CMFC下拉工具栏：：更新CmdUI](#onupdatecmdui)|（覆盖[CMFCTool 栏：更新 CmdUI](cmfctoolbar-class.md)。|

### <a name="remarks"></a>备注

对象`CMFCDropDownToolBar`将工具栏的视觉外观与弹出菜单的行为相结合。 当用户按下并持有下拉工具栏按钮（请参阅[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)）时，将显示一个下拉工具栏，用户可以通过滚动到下拉工具栏并释放鼠标按钮来从下拉工具栏中选择一个按钮。 用户选择下拉工具栏中的按钮后，该按钮将显示为顶部工具栏上的当前按钮。

无法自定义或停靠下拉工具栏，并且没有拆解状态。

下图显示了一个`CMFCDropDownToolBar`对象：

![CMFCDropDownToolbar 示例](../../mfc/reference/media/cmfcdropdown.png "CMFCDropDownToolbar 示例")

创建`CMFCDropDownToolBar`对象的方式与创建普通工具栏的方式相同（请参阅[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)）。

要将下拉工具栏插入父工具栏：：

1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。

2. 创建包含`CMFCDropDownToolBarButton`下拉工具栏的对象（有关详细信息，请参阅[CMFCDrop 下拉工具栏按钮：：CMFC下拉下工具栏按钮](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)）。

3. 使用 CMFCToolBar`CMFCDropDownToolBarButton`将虚拟按钮替换为对象[：：替换按钮](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。

有关工具栏按钮的详细信息，请参阅[演练：将控件放在工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 有关下拉工具栏的示例，请参阅示例项目 VisualStudioDemo。

## <a name="example"></a>示例

下面的示例演示如何在`Create``CMFCDropDownToolBar`类中使用 方法。 此代码段是[可视化工作室演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具栏](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>要求

**标头：** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFC向下工具栏：：允许显示帕内菜单

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcdropdowntoolbarloadbitmap"></a><a name="loadbitmap"></a>CMFC下拉工具栏：：加载位图

从应用程序资源加载工具栏图像。

```
virtual BOOL LoadBitmap(
    UINT uiResID,
    UINT uiColdResID=0,
    UINT uiMenuResID=0,
    BOOL bLocked=FALSE,
    UINT uiDisabledResID=0,
    UINT uiMenuDisabledResID=0);
```

### <a name="parameters"></a>参数

*uiResID*<br/>
[在]引用热工具栏图像的位图的资源 ID。

*乌伊库德雷斯ID*<br/>
[在]引用冷工具栏图像的位图的资源 ID。

*uiMenuResID*<br/>
[在]引用常规菜单图像的位图的资源 ID。

*封锁*<br/>
[在]锁定工具栏的 TRUE;否则 FALSE。

*ui禁用雷斯ID*<br/>
[在]引用禁用工具栏图像的位图的资源 ID。

*uiMenu 禁用雷斯 ID*<br/>
[在]引用禁用菜单图像的位图的资源 ID。

### <a name="return-value"></a>返回值

如果该方法成功，则为非零；否则为零。

### <a name="remarks"></a>备注

[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) 方法调用此方法以加载与工具栏关联的图像。 重写此方法以执行图像资源的自定义加载。

调用 `LoadBitmapEx` 方法以在创建工具栏后加载其他图像。

## <a name="cmfcdropdowntoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CMFC下拉工具栏：：加载工具栏

```
virtual BOOL LoadToolBar(
    UINT uiResID,
    UINT uiColdResID = 0,
    UINT uiMenuResID = 0,
    BOOL = FALSE,
    UINT uiDisabledResID = 0,
    UINT uiMenuDisabledResID = 0,
    UINT uiHotResID = 0);
```

### <a name="parameters"></a>参数

[在]*uiResID*<br/>

[在]*乌伊库德雷斯ID*<br/>

[在]*uiMenuResID*<br/>

[在]*波尔*<br/>

[在]*ui禁用雷斯ID*<br/>

[在]*uiMenu 禁用雷斯 ID*<br/>

[在]*乌霍特雷斯ID*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcdropdowntoolbaronlbuttonup"></a><a name="onlbuttonup"></a>CMFC下拉工具栏：：在LButtonup上

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>参数

[在]*nFlags*<br/>

[在]*点*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcdropdowntoolbaronmousemove"></a><a name="onmousemove"></a>CMFC向下工具栏：：鼠标移动

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>参数

[在]*nFlags*<br/>

[在]*点*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcdropdowntoolbaronsendcommand"></a><a name="onsendcommand"></a>CMFC下拉工具栏：打开发送命令

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>参数

[在]*pButton*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcdropdowntoolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFC下拉工具栏：：更新CmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>参数

[在]*p目标*<br/>

[在]*b 禁用IfNoHndler*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFC工具栏：创建](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFC工具栏：更换按钮](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
