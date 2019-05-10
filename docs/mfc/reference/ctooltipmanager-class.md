---
title: CTooltipManager 类
ms.date: 11/04/2016
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
ms.openlocfilehash: e8b88f2722f5a4379276f13c2ef159aa4d120533
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323747"
---
# <a name="ctooltipmanager-class"></a>CTooltipManager 类

维护有关工具提示的运行时信息。 `CTooltipManager` 类在每个应用程序中实例化一次。

## <a name="syntax"></a>语法

```
class CTooltipManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CTooltipManager::CreateToolTip](#createtooltip)|为指定的 Windows 控件类型创建工具提示控件。|
|[CTooltipManager::DeleteToolTip](#deletetooltip)|删除工具提示控件。|
|[CTooltipManager::SetTooltipParams](#settooltipparams)|自定义指定 Windows 控件类型工具提示的可视外观。|
|[CTooltipManager::SetTooltipText](#settooltiptext)|设置工具提示控件的文本和说明。|
|[CTooltipManager::UpdateTooltips](#updatetooltips)||

## <a name="remarks"></a>备注

使用[CMFCToolTipCtrl 类](../../mfc/reference/cmfctooltipctrl-class.md)， `CMFCToolTipInfo`，和`CTooltipManager`以你的应用程序中实现自定义工具提示。 有关如何使用这些工具提示类的示例，请参阅[CMFCToolTipCtrl 类](../../mfc/reference/cmfctooltipctrl-class.md)主题。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>要求

**标头：** afxtooltipmanager.h

##  <a name="createtooltip"></a>  CTooltipManager::CreateToolTip

创建工具提示控件。

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>参数

*pToolTip*<br/>
[out]工具提示指针的引用。 它是设置为时该函数将返回指向新创建的工具提示。

*pWndParent*<br/>
[in]在工具提示的父级。

*nType*<br/>
[in]在工具提示的类型。

### <a name="return-value"></a>返回值

如果已成功创建工具提示，非零值。

### <a name="remarks"></a>备注

必须调用[CTooltipManager::DeleteToolTip](#deletetooltip)若要删除的工具提示控件将传回到*pToolTip*。

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)设置工具提示的视觉显示参数，它会创建每个工具提示的基础类型的*n 类型*指定。 若要更改一个或多个工具提示类型的参数，请调用[ctooltipmanager:: Settooltipparams](#settooltipparams)。

下表中列出了有效的工具提示类型：

|工具提示类型|控件类别|示例类型|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|一个按钮。|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|标题栏。|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|任何不符合另一种类别的控件。|无。|
|AFX_TOOLTIP_TYPE_DOCKBAR|可停靠的窗格。|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|文本框。|无。|
|AFX_TOOLTIP_TYPE_MINIFRAME|袖珍框架。|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|规划器。|无。|
|AFX_TOOLTIP_TYPE_RIBBON|功能区栏。|CMFCRibbonBar, CMFCRibbonPanelMenuBar|
|AFX_TOOLTIP_TYPE_TAB|选项卡控件。|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|一个工具栏。|CMFCToolBar, CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|工具箱。|无。|

##  <a name="deletetooltip"></a>  CTooltipManager::DeleteToolTip

删除工具提示控件。

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>参数

*pToolTip*<br/>
[in、 out]对指向要销毁的工具提示的指针的引用。

### <a name="remarks"></a>备注

调用此方法为每个[CToolTipCtrl 类](../../mfc/reference/ctooltipctrl-class.md)创建的[CTooltipManager::CreateToolTip](#createtooltip)。 父控件应调用此方法从其`OnDestroy`处理程序。 这需要从 framework 正确删除工具提示。 此方法设置*pToolTip*为之前它将返回 NULL。

##  <a name="settooltipparams"></a>  CTooltipManager::SetTooltipParams

自定义指定的 Windows 控件类型的工具提示控件的外观。

```
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>参数

*nTypes*<br/>
[in]指定控件类型。

*pRTC*<br/>
[in]自定义工具提示的运行时类。

*pParams*<br/>
[in]工具提示的参数。

### <a name="remarks"></a>备注

此方法设置的运行时类和初始参数的[CToolTipManager](../../mfc/reference/ctooltipmanager-class.md)创建工具提示时使用。 当控件调用[CTooltipManager::CreateToolTip](#createtooltip)和工具提示中将类型传递，它是一种类型由指示*nTypes*，工具提示管理器创建的一个实例的工具提示控件指定的运行时类*pRTC* ，并将指定的参数传递*pParams*到新的工具提示。

在调用此方法，所有现有的工具提示所有者收到 AFX_WM_UPDATETOOLTIPS 消息并且它们必须通过使用重新创建相应的工具提示[CTooltipManager::CreateToolTip](#createtooltip)。

*nTypes*可以是有效的工具提示的任意组合类型[CTooltipManager::CreateToolTip](#createtooltip)使用，也可以是 AFX_TOOLTIP_TYPE_ALL。 如果通过 AFX_TOOLTIP_TYPE_ALL，所有工具提示类型会受到影响。

### <a name="example"></a>示例

下面的示例演示如何使用`SetTooltipParams`方法的`CTooltipManager`类。 此代码片段属于 [Draw Client 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

##  <a name="settooltiptext"></a>  CTooltipManager::SetTooltipText

设置文本和工具提示的说明。

```
static void SetTooltipText(
    TOOLINFO* pTI,
    CToolTipCtrl* pToolTip,
    UINT nType,
    const CString strText,
    LPCTSTR lpszDescr=NULL);
```

### <a name="parameters"></a>参数

*pTI*<br/>
[in]指向 TOOLINFO 对象的指针。

*pToolTip*<br/>
[in、 out]指向要为其设置的文本和说明的工具提示控件的指针。

*nType*<br/>
[in]指定该工具提示与之关联的控件的类型。

*strText*<br/>
[in]要将设置为工具提示文本的文本。

*lpszDescr*<br/>
[in]指向的工具提示说明的指针。 可以为 NULL。

### <a name="remarks"></a>备注

值*n 类型*必须是相同的值*n 类型*参数[CTooltipManager::CreateToolTip](#createtooltip)时创建工具提示。

##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

```
void UpdateTooltips();
```

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl 类](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)
