---
title: CMFCTasksPaneTaskGroup 类
ms.date: 11/19/2018
f1_keywords:
- CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsBottom
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsCollapsed
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsSpecial
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_lstTasks
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rect
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rectGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_strName
helpviewer_keywords:
- CMFCTasksPaneTaskGroup [MFC], CMFCTasksPaneTaskGroup
- CMFCTasksPaneTaskGroup [MFC], SetACCData
- CMFCTasksPaneTaskGroup [MFC], m_bIsBottom
- CMFCTasksPaneTaskGroup [MFC], m_bIsCollapsed
- CMFCTasksPaneTaskGroup [MFC], m_bIsSpecial
- CMFCTasksPaneTaskGroup [MFC], m_lstTasks
- CMFCTasksPaneTaskGroup [MFC], m_rect
- CMFCTasksPaneTaskGroup [MFC], m_rectGroup
- CMFCTasksPaneTaskGroup [MFC], m_strName
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
ms.openlocfilehash: a28f00fb732727ec1334946a9e752679307cd3a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222217"
---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup 类

`CMFCTasksPaneTaskGroup`类是由一个帮助器类[CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)控件。 `CMFCTasksPaneTaskGroup` 类型的对象表示一个任务组 。 任务组是框架在具有折叠按钮的单独框中显示的项列表。 此框可具有一个可选标题（组名）。 如果一个组处于折叠状态，则任务列表不可见。

## <a name="syntax"></a>语法

```
class CMFCTasksPaneTaskGroup : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|构造 `CMFCTasksPaneTaskGroup` 对象。|
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|确定当前的任务组的可访问性数据。|

### <a name="data-members"></a>数据成员

|名称|描述|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|确定是否将任务组对齐到任务窗格控件的底部。|
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|确定任务组处于折叠状态。|
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|确定是否为任务组*特殊。* 框架显示不同的颜色的特殊隐藏式字幕。|
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|包含任务的内部列表。|
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|指定的组标题的边框。|
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|指定组的边界矩形。|
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|指定组的名称。|

## <a name="remarks"></a>备注

下图显示了展开的任务组：

![任务组中，展开](../../mfc/reference/media/nexttaskgrpexpand.png "展开任务组")

下图显示了已折叠的任务组：

![折叠任务组](../../mfc/reference/media/nexttaskgrpcollapse.png "折叠任务组")

下图显示了不带标题的任务组：

![无标题的任务组](../../mfc/reference/media/nexttaskgrpnocapt.png "无标题的任务组")

下图显示两个任务组。 通过设置的标记的第一个任务组特殊`m_bIsSpecial`标记，用于为 TRUE，而第二个任务组并不特殊。 请注意第一个任务组的标题是比第二个任务组暗：

![特殊任务组](../../mfc/reference/media/nexttaskgrpspecial.png "特殊任务组")

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)

## <a name="requirements"></a>要求

**标头：** afxTasksPane.h

##  <a name="cmfctaskspanetaskgroup"></a>  CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup

构造 `CMFCTasksPaneTaskGroup` 对象。

```
CMFCTasksPaneTaskGroup(
    LPCTSTR lpszName,
    BOOL bIsBottom,
    BOOL bIsSpecial=FALSE,
    BOOL bIsCollapsed=FALSE,
    CMFCTasksPanePropertyPage* pPage=NULL,
    HICON hIcon=NULL);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
组标题中指定的组的名称。

*bIsBottom*<br/>
指定是否在组到任务窗格控件的底部对齐。

*bIsSpecial*<br/>
指定是否在组指定为*特殊*，因此，是否填充的组标题与不同的颜色。

*bIsCollapsed*<br/>
指定组处于折叠状态。

*pPage*<br/>
指定此任务组所属的属性页。

*hIcon*<br/>
指定在组标题中显示的图标。

### <a name="remarks"></a>备注

##  <a name="m_bisbottom"></a>  CMFCTasksPaneTaskGroup::m_bIsBottom

确定是否将任务组对齐到任务窗格控件的底部。

```
BOOL m_bIsBottom;
```

### <a name="remarks"></a>备注

只有一个组可以对齐到任务窗格控件的底部。 此任务组必须添加最后一个。 有关详细信息，请参阅[cmfctaskspane:: Addgroup](../../mfc/reference/cmfctaskspane-class.md#addgroup)。

##  <a name="m_biscollapsed"></a>  CMFCTasksPaneTaskGroup::m_bIsCollapsed

确定任务组处于折叠状态。

```
BOOL m_bIsCollapsed;
```

### <a name="remarks"></a>备注

可以启用或禁用的功能上任务窗格中的折叠组通过调用[cmfctaskspane:: Enablegroupcollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse)。

##  <a name="m_bisspecial"></a>  CMFCTasksPaneTaskGroup::m_bIsSpecial

确定是否为任务组*特殊*，是否应通过不同的颜色标识特殊任务组的标题。

```
BOOL m_bIsSpecial;
```

### <a name="remarks"></a>备注

如果应用程序使用 Windows XP 视觉主题以及`m_bIsSpecial`为 FALSE 时，框架将调用`DrawThemeBackground`EBP_NORMALGROUPBACKGROUND 标志。 如果`m_bIsSpecial`为 TRUE，框架将调用`DrawThemeBackground`EBP_SPECIALGROUPBACKGROUND 标志。

##  <a name="m_lsttasks"></a>  CMFCTasksPaneTaskGroup::m_lstTasks

包含任务的内部列表。

```
CObList m_lstTasks;
```

### <a name="remarks"></a>备注

若要填充此列表，请调用[cmfctaskspane:: Addtask](../../mfc/reference/cmfctaskspane-class.md#addtask)。

##  <a name="m_rect"></a>  CMFCTasksPaneTaskGroup::m_rect

指定的组标题的边框。

```
CRect m_rect;
```

### <a name="remarks"></a>备注

由框架自动计算此值。

##  <a name="m_rectgroup"></a>  CMFCTasksPaneTaskGroup::m_rectGroup

指定组的边界矩形。

```
CRect m_rectGroup;
```

### <a name="remarks"></a>备注

由框架自动计算此值。

##  <a name="m_strname"></a>  CMFCTasksPaneTaskGroup::m_strName

指定组的名称。

```
CString m_strName;
```

### <a name="remarks"></a>备注

如果此值为空，不显示组标题，并且不能折叠组。

##  <a name="setaccdata"></a>  CMFCTasksPaneTaskGroup::SetACCData

确定当前的任务组的可访问性数据。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*pParent*<br/>
[in]表示当前的任务组的父窗口。

*data*<br/>
[out]类型的对象`CAccessibilityData`并且填充了当前的任务组的可访问性数据。

### <a name="return-value"></a>返回值

则为 TRUE*数据*参数已成功使用当前的任务组的可访问性数据填充; 否则为 FALSE。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTasksPane 类](../../mfc/reference/cmfctaskspane-class.md)<br/>
[CMFCTasksPaneTask 类](../../mfc/reference/cmfctaskspanetask-class.md)<br/>
[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)
