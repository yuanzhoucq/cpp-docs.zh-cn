---
title: CMFCDropDownToolBar 类 |Microsoft Docs
ms.custom: ''
ms.date: 10/188/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d781cb78b1dce9f7ab3580e7acd32e3e6dbac55
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063336"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar 类

当用户按住顶层工具栏按钮时显示的工具栏。

   有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。
## <a name="syntax"></a>语法

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|（重写 `CPane::AllowShowOnPaneMenu`。）|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(重写[CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap)。)|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(重写[CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar)。)|
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|（重写 `CMFCToolBar::OnSendCommand`。）|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(重写[CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md)。|

### <a name="remarks"></a>备注

一个`CMFCDropDownToolBar`对象将弹出菜单的行为与相结合的可视外观的工具栏。 当用户按下并包含一个下拉工具栏按钮 (请参阅[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md))、 下拉工具栏将出现，并且用户可以通过滚动到并释放鼠标从下拉列表工具栏中选择一个按钮按钮。 用户在下拉工具栏中选择某个按钮后，该按钮显示为顶层工具栏上的当前按钮。

不能自定义下拉工具栏或停靠，并不具有拖曳状态。

下图显示`CMFCDropDownToolBar`对象：

![Cmfcdropdowntoolbar 示例](../../mfc/reference/media/cmfcdropdown.png "cmfcdropdown")

您创建`CMFCDropDownToolBar`对象创建普通的工具栏上的相同方式 (请参阅[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md))。

要插入到在父级工具栏的下拉工具栏：

1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。

2. 创建`CMFCDropDownToolBarButton`对象，其中包含下拉工具栏 (有关详细信息，请参阅[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton))。

3. 替换为与将虚拟按钮`CMFCDropDownToolBarButton`通过使用对象[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。

有关工具栏按钮的详细信息，请参阅[演练： 将置于工具栏上的控件](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 下拉工具栏的示例，请参阅示例项目 VisualStudioDemo。

## <a name="example"></a>示例

下面的示例演示如何使用`Create`中的方法`CMFCDropDownToolBar`类。 此代码片段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>要求

**标头：** afxdropdowntoolbar.h

##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap

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
[in]用于引用热工具栏图像的位图资源 ID。

*uiColdResID*<br/>
[in]用于引用冷工具栏图像的位图资源 ID。

*uiMenuResID*<br/>
[in]用于引用常规菜单图像的位图资源 ID。

*被阻止*<br/>
[in]为 TRUE，则锁定工具栏;否则为 FALSE。

*uiDisabledResID*<br/>
[in]用于引用禁用的工具栏图像的位图资源 ID。

*uiMenuDisabledResID*<br/>
[in]用于引用禁用的菜单图像的位图资源 ID。

### <a name="return-value"></a>返回值

如果该方法成功，则为非零；否则为零。

### <a name="remarks"></a>备注

[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) 方法调用此方法以加载与工具栏关联的图像。 重写此方法以执行图像资源的自定义加载。

调用 `LoadBitmapEx` 方法以在创建工具栏后加载其他图像。

##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar

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

[in]*uiResID*<br/>

[in]*uiColdResID*<br/>

[in]*uiMenuResID*<br/>

[in]*BOOL*<br/>

[in]*uiDisabledResID*<br/>

[in]*uiMenuDisabledResID*<br/>

[in]*uiHotResID*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>参数

[in]*nFlags*<br/>

[in]*点*<br/>

### <a name="remarks"></a>备注

##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>参数

[in]*nFlags*<br/>

[in]*点*<br/>

### <a name="remarks"></a>备注

##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>参数

[in]*pButton*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>参数

[in]*pTarget*<br/>

[in]*bDisableIfNoHndler*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton 类](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)

