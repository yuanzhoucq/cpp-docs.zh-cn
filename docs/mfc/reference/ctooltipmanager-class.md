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
ms.openlocfilehash: 37fcf47b7537e89974a61e6c50c41e164d555678
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365077"
---
# <a name="ctooltipmanager-class"></a>CTooltipManager 类

维护有关工具提示的运行时信息。 `CTooltipManager` 类在每个应用程序中实例化一次。

## <a name="syntax"></a>语法

```
class CTooltipManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CTooltipManager::CreateToolTip](#createtooltip)|为指定的 Windows 控件类型创建工具提示控件。|
|[CTooltipManager::DeleteToolTip](#deletetooltip)|删除工具提示控件。|
|[CTooltipManager::SetTooltipParams](#settooltipparams)|自定义指定 Windows 控件类型工具提示的可视外观。|
|[CTooltipManager::SetTooltipText](#settooltiptext)|设置工具提示控件的文本和说明。|
|[CTooltipManager::UpdateTooltips](#updatetooltips)||

## <a name="remarks"></a>备注

使用[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)`CMFCToolTipInfo`类`CTooltipManager`，并一起实现应用程序中的自定义工具提示。 有关如何使用这些工具提示类的示例，请参阅[CMFCToolTipCtrl 类主题](../../mfc/reference/cmfctooltipctrl-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>要求

**标题：** afxtooltip管理器.h

## <a name="ctooltipmanagercreatetooltip"></a><a name="createtooltip"></a>CTooltip管理器：创建工具提示

创建工具提示控件。

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>参数

*pToolTip*<br/>
[出]对工具提示指针的引用。 当函数返回时，它将指向新创建的工具提示。

*pwnd 父级*<br/>
[在]工具提示的父级。

nType**<br/>
[在]工具提示的类型。

### <a name="return-value"></a>返回值

如果已成功创建工具提示，则非零。

### <a name="remarks"></a>备注

您必须调用[CTooltipManager：:DeleteToolTip](#deletetooltip)删除在*pToolTip*中传递的工具提示控件。

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)根据*nType*指定的工具提示类型设置它创建的每个工具提示的可视显示参数。 要更改一个或多个工具提示类型的参数，请致电[CTooltipManager：：设置工具提示Params](#settooltipparams)。

下表列出了有效的工具提示类型：

|工具提示类型|控制类别|示例类型|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|一个按钮。|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|标题栏。|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|不适合其他类别的任何控件。|无。|
|AFX_TOOLTIP_TYPE_DOCKBAR|可停靠窗格。|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|文本框。|无。|
|AFX_TOOLTIP_TYPE_MINIFRAME|小型框架。|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|规划师|无。|
|AFX_TOOLTIP_TYPE_RIBBON|带状栏。|CMFC丝带栏，CMFC丝带面板菜单栏|
|AFX_TOOLTIP_TYPE_TAB|选项卡控件。|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|工具栏。|CMFC工具栏，CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|工具箱。|无。|

## <a name="ctooltipmanagerdeletetooltip"></a><a name="deletetooltip"></a>CTooltip管理器：:DeleteTooltip

删除工具提示控件。

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>参数

*pToolTip*<br/>
[进出]指向要销毁的工具提示的指针的引用。

### <a name="remarks"></a>备注

调用此方法的每个[CToolTipCtrl 类](../../mfc/reference/ctooltipctrl-class.md)由[CTooltipManager 创建：：创建工具提示](#createtooltip)。 父控件应从其`OnDestroy`处理程序调用此方法。 这是正确从框架中删除工具提示所必需的。 此方法在返回之前将*pToolTip*设置为 NULL。

## <a name="ctooltipmanagersettooltipparams"></a><a name="settooltipparams"></a>CTooltip管理器：：设置工具提示

自定义指定 Windows 控件类型的工具提示控件的外观。

```
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>参数

*n 类型*<br/>
[在]指定控件类型。

*pRTC*<br/>
[在]自定义工具提示的运行时类。

*pParams*<br/>
[在]工具提示参数。

### <a name="remarks"></a>备注

此方法设置[CToolTipManager](../../mfc/reference/ctooltipmanager-class.md)在创建工具提示时使用的运行时类和初始参数。 当控件调用[CTooltipManager：：CreateTooltip](#createtooltip)并传递工具提示类型（这是*nTypes*指示的类型之一），工具提示管理器将创建一个工具提示控件，该控件是*pRTC*指定的运行时类的实例，并将*pParams*指定的参数传递给新的工具提示。

调用此方法时，所有现有的工具提示所有者都会收到AFX_WM_UPDATETOOLTIPS消息，他们必须使用[CTooltipManager：：：createToolTip](#createtooltip)重新创建工具提示。

*nTypes*可以是[CTooltipManager 使用的有效工具提示类型的任意组合：创建工具提示](#createtooltip)，也可以AFX_TOOLTIP_TYPE_ALL。 如果传递AFX_TOOLTIP_TYPE_ALL，则所有工具提示类型都受到影响。

### <a name="example"></a>示例

下面的示例演示如何使用`SetTooltipParams``CTooltipManager`类的方法。 此代码片段属于 [Draw Client 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

## <a name="ctooltipmanagersettooltiptext"></a><a name="settooltiptext"></a>CTooltip管理器：：设置工具提示文本

设置工具提示的文本和说明。

```
static void SetTooltipText(
    TOOLINFO* pTI,
    CToolTipCtrl* pToolTip,
    UINT nType,
    const CString strText,
    LPCTSTR lpszDescr=NULL);
```

### <a name="parameters"></a>参数

*Pti*<br/>
[在]指向 TOOLINFO 对象的指针。

*pToolTip*<br/>
[进出]指向工具提示控件的指针，用于设置文本和说明。

nType**<br/>
[在]指定与此工具提示关联的控件类型。

*斯特文本*<br/>
[在]要设置为工具提示文本的文本。

*lpszDescr*<br/>
[在]指向工具提示说明的指针。 可以为 NULL。

### <a name="remarks"></a>备注

*nType*的值必须与[CTooltipManager 的](#createtooltip) *nType*参数的值相同：创建工具提示时创建工具提示。

## <a name="ctooltipmanagerupdatetooltips"></a><a name="updatetooltips"></a>CTool提示管理器：：更新工具提示

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
void UpdateTooltips();
```

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl 类](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCTool提示信息类](../../mfc/reference/cmfctooltipinfo-class.md)
