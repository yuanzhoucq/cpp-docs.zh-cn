---
title: CMFC任务窗格任务组类
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
ms.openlocfilehash: 4c24eba646bede462a5f3cfb85715278cfa7daee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366256"
---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFC任务窗格任务组类

该`CMFCTasksPaneTaskGroup`类是[CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)控件使用的帮助器类。 `CMFCTasksPaneTaskGroup` 类型的对象表示一个任务组 **。 任务组是框架在具有折叠按钮的单独框中显示的项列表。 此框可具有一个可选标题（组名）。 如果一个组处于折叠状态，则任务列表不可见。

## <a name="syntax"></a>语法

```
class CMFCTasksPaneTaskGroup : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC任务窗格任务组：：CMFC任务窗格任务组](#cmfctaskspanetaskgroup)|构造 `CMFCTasksPaneTaskGroup` 对象。|
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC任务窗格任务组：：设置ACC数据](#setaccdata)|确定当前任务组的辅助功能数据。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFC任务窗格任务组：：m_bIsBottom](#m_bisbottom)|确定任务组是否与任务窗格控件的底部对齐。|
|[CMFC任务窗格任务组：：m_bIsCollapsed](#m_biscollapsed)|确定任务组是否折叠。|
|[CMFC任务窗格任务组：：m_bIsSpecial](#m_bisspecial)|确定任务组是否*特殊。* 框架以不同颜色显示特殊标题。|
|[CMFC任务窗格任务组：：m_lstTasks](#m_lsttasks)|包含任务的内部列表。|
|[CMFC任务窗格任务组：：m_rect](#m_rect)|指定组标题的边界矩形。|
|[CMFC任务窗格任务组：：m_rectGroup](#m_rectgroup)|指定组的边界矩形。|
|[CMFC任务窗格任务组：：m_strName](#m_strname)|指定组的名称。|

## <a name="remarks"></a>备注

下图显示了展开的任务组：

![已展开的任务组](../../mfc/reference/media/nexttaskgrpexpand.png "已展开的任务组")

下图显示了折叠的任务组：

![已折叠的任务组](../../mfc/reference/media/nexttaskgrpcollapse.png "已折叠的任务组")

下图显示了没有标题的任务组：

![无标题的任务组](../../mfc/reference/media/nexttaskgrpnocapt.png "无标题的任务组")

下图显示了两个任务组。 通过将`m_bIsSpecial`标志设置为 TRUE，将第一个任务组标记为特殊，而第二个任务组不特殊。 请注意第一个任务组的标题如何比第二个任务组暗：

![特殊任务组](../../mfc/reference/media/nexttaskgrpspecial.png "特殊任务组")

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)

## <a name="requirements"></a>要求

**标题：** afxTasksPane.h

## <a name="cmfctaskspanetaskgroupcmfctaskspanetaskgroup"></a><a name="cmfctaskspanetaskgroup"></a>CMFC任务窗格任务组：：CMFC任务窗格任务组

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

*lpsz名称*<br/>
在组标题中指定组的名称。

*bIsBottom*<br/>
指定组是否与任务窗格控件的底部对齐。

*b 特别*<br/>
指定组是否指定为*特殊*，因此，组标题是否以不同颜色填充。

*bIs 折叠*<br/>
指定组是否折叠。

*pPage*<br/>
指定此任务组所属的属性页。

*hIcon*<br/>
指定在组标题中显示的图标。

### <a name="remarks"></a>备注

## <a name="cmfctaskspanetaskgroupm_bisbottom"></a><a name="m_bisbottom"></a>CMFC任务窗格任务组：：m_bIsBottom

确定任务组是否与任务窗格控件的底部对齐。

```
BOOL m_bIsBottom;
```

### <a name="remarks"></a>备注

只能将一个组与任务窗格控件的底部对齐。 必须最后添加此任务组。 有关详细信息，请参阅[CMFC任务窗格：：添加组](../../mfc/reference/cmfctaskspane-class.md#addgroup)。

## <a name="cmfctaskspanetaskgroupm_biscollapsed"></a><a name="m_biscollapsed"></a>CMFC任务窗格任务组：：m_bIsCollapsed

确定任务组是否折叠。

```
BOOL m_bIsCollapsed;
```

### <a name="remarks"></a>备注

您可以通过调用[CMFCTasksPane：：启用组折叠](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse)来启用或禁用在任务窗格上折叠组的能力。

## <a name="cmfctaskspanetaskgroupm_bisspecial"></a><a name="m_bisspecial"></a>CMFC任务窗格任务组：：m_bIsSpecial

确定任务组是否*特殊*，以及是否应以不同颜色标识特殊任务组的标题。

```
BOOL m_bIsSpecial;
```

### <a name="remarks"></a>备注

如果应用程序使用 Windows XP 可视主题，并且`m_bIsSpecial`为 FALSE，则框架`DrawThemeBackground`将使用EBP_NORMALGROUPBACKGROUND标志调用。 如果`m_bIsSpecial`为 TRUE，则框架`DrawThemeBackground`使用EBP_SPECIALGROUPBACKGROUND标志调用。

## <a name="cmfctaskspanetaskgroupm_lsttasks"></a><a name="m_lsttasks"></a>CMFC任务窗格任务组：：m_lstTasks

包含任务的内部列表。

```
CObList m_lstTasks;
```

### <a name="remarks"></a>备注

要填写此列表，请致电[CMFC任务窗格：：添加任务](../../mfc/reference/cmfctaskspane-class.md#addtask)。

## <a name="cmfctaskspanetaskgroupm_rect"></a><a name="m_rect"></a>CMFC任务窗格任务组：：m_rect

指定组标题的边界矩形。

```
CRect m_rect;
```

### <a name="remarks"></a>备注

此值由框架自动计算。

## <a name="cmfctaskspanetaskgroupm_rectgroup"></a><a name="m_rectgroup"></a>CMFC任务窗格任务组：：m_rectGroup

指定组的边界矩形。

```
CRect m_rectGroup;
```

### <a name="remarks"></a>备注

此值由框架自动计算。

## <a name="cmfctaskspanetaskgroupm_strname"></a><a name="m_strname"></a>CMFC任务窗格任务组：：m_strName

指定组的名称。

```
CString m_strName;
```

### <a name="remarks"></a>备注

如果此值为空，则不显示组标题，并且无法折叠组。

## <a name="cmfctaskspanetaskgroupsetaccdata"></a><a name="setaccdata"></a>CMFC任务窗格任务组：：设置ACC数据

确定当前任务组的辅助功能数据。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*p 父级*<br/>
[在]表示当前任务组的父窗口。

*数据*<br/>
[出]使用当前任务组的`CAccessibilityData`辅助功能数据填充的类型对象。

### <a name="return-value"></a>返回值

如果*数据*参数已成功填充当前任务组的辅助功能数据，则为 TRUE;否则，FALSE。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC任务窗格类](../../mfc/reference/cmfctaskspane-class.md)<br/>
[CMFC任务窗格任务类](../../mfc/reference/cmfctaskspanetask-class.md)<br/>
[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)
