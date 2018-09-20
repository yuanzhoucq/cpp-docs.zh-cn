---
title: CMFCTasksPaneTask 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTask::m_bAutoDestroyWindow
- AFXTASKSPANE/CMFCTasksPaneTask::m_bIsBold
- AFXTASKSPANE/CMFCTasksPaneTask::m_dwUserData
- AFXTASKSPANE/CMFCTasksPaneTask::m_hwndTask
- AFXTASKSPANE/CMFCTasksPaneTask::m_nIcon
- AFXTASKSPANE/CMFCTasksPaneTask::m_nWindowHeight
- AFXTASKSPANE/CMFCTasksPaneTask::m_pGroup
- AFXTASKSPANE/CMFCTasksPaneTask::m_rect
- AFXTASKSPANE/CMFCTasksPaneTask::m_strName
- AFXTASKSPANE/CMFCTasksPaneTask::m_uiCommandID
dev_langs:
- C++
helpviewer_keywords:
- CMFCTasksPaneTask [MFC], CMFCTasksPaneTask
- CMFCTasksPaneTask [MFC], SetACCData
- CMFCTasksPaneTask [MFC], m_bAutoDestroyWindow
- CMFCTasksPaneTask [MFC], m_bIsBold
- CMFCTasksPaneTask [MFC], m_dwUserData
- CMFCTasksPaneTask [MFC], m_hwndTask
- CMFCTasksPaneTask [MFC], m_nIcon
- CMFCTasksPaneTask [MFC], m_nWindowHeight
- CMFCTasksPaneTask [MFC], m_pGroup
- CMFCTasksPaneTask [MFC], m_rect
- CMFCTasksPaneTask [MFC], m_strName
- CMFCTasksPaneTask [MFC], m_uiCommandID
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0bc6a9a1bfe527015a0782a625600ea1b9ade76
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422997"
---
# <a name="cmfctaskspanetask-class"></a>CMFCTasksPaneTask 类

`CMFCTasksPaneTask`类是表示任务的任务窗格控件的帮助器类 ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md))。 任务对象表示任务组中的项 ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md))。 每个任务可具有在用户单击任务和显示在任务名称左侧的图标时框架所执行的命令。

## <a name="syntax"></a>语法

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCTasksPaneTask::CMFCTasksPaneTask](#cmfctaskspanetask)|创建并初始化`CMFCTasksPaneTask`对象。|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|确定当前任务的可访问性数据。|

### <a name="data-members"></a>数据成员

|name|描述|
|----------|-----------------|
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|确定是否自动销毁任务窗口。|
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|确定是否该框架在绘制任务标签显示为粗体文本。|
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|包含 framework 将与任务相关联的用户定义数据。 如果该任务有没有关联的数据，设置为零。|
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|任务窗口的句柄。|
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|框架的任务旁显示的图像的图像列表中的索引。|
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|任务窗口的高度。 如果该任务有没有任务窗口，此值为零。|
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|一个指向`CMFCTasksPaneTaskGroup`属于此任务。|
|[CMFCTasksPaneTask::m_rect](#m_rect)|指定该任务的边界矩形。|
|[CMFCTasksPaneTask::m_strName](#m_strname)|任务的名称。|
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|指定在用户单击该任务时框架所执行的命令的命令 ID。 如果此值不是有效的命令 ID，该任务视为一个简单的标签。|

## <a name="remarks"></a>备注

下图显示了包含三个任务的任务组：

![任务组中，展开](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")

> [!NOTE]
>  如果任务不具有有效的命令 ID，则将它视为一个简单的标签。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>要求

**标头：** afxTasksPane.h

##  <a name="cmfctaskspanetask"></a>  CMFCTasksPaneTask::CMFCTasksPaneTask

创建并初始化`CMFCTasksPaneTask`对象。

```
CMFCTasksPaneTask(
    CMFCTasksPaneTaskGroup* pGroup,
    LPCTSTR lpszName,
    int nIcon,
    UINT uiCommandID,
    DWORD dwUserData = 0,
    HWND hwndTask = NULL,
    BOOL bAutoDestroyWindow = FALSE,
    int nWindowHeight = 0);
```

### <a name="parameters"></a>参数

*pGroup*<br/>
指定[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)所属的任务。

*lpszName*<br/>
指定任务的名称。

*nIcon*<br/>
图像列表中指定任务的图像的索引。

*uiCommandID*<br/>
指定单击该任务时执行的命令的命令 ID。

*dwUserData*<br/>
用户定义的数据。

*hwndTask*<br/>
指定任务窗口的句柄。

*bAutoDestroyWindow*<br/>
如果为 TRUE，任务窗口将自动销毁。

*nWindowHeight*<br/>
指定的任务窗口的高度。

### <a name="remarks"></a>备注

##  <a name="m_bautodestroywindow"></a>  CMFCTasksPaneTask::m_bAutoDestroyWindow

确定是否自动销毁任务窗口。

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>备注

设置为 TRUE，以指定的任务窗口 ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) 自动; 否则为 FALSE 时被销毁。

##  <a name="m_bisbold"></a>  CMFCTasksPaneTask::m_bIsBold

确定是否显示为粗体文本绘制任务标签。

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>备注

设置此成员为 true，则显示为加粗任务标签的文本。

##  <a name="m_dwuserdata"></a>  CMFCTasksPaneTask::m_dwUserData

包含与任务相关联的用户定义数据。 如果没有任何数据与任务关联，则设置为零。

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>备注

##  <a name="m_hwndtask"></a>  CMFCTasksPaneTask::m_hwndTask

任务窗口的句柄。

```
HWND m_hwndTask;
```

### <a name="remarks"></a>备注

若要添加的任务窗口，请调用[CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow)。

##  <a name="m_nicon"></a>  CMFCTasksPaneTask::m_nIcon

标识指定的任务的旁边显示的图像的图像列表中的索引位置。

```
int m_nIcon;
```

### <a name="remarks"></a>备注

设置图像列表[CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist)。

设置`m_nIcon`为-1，如果你想要显示图像的任务。

##  <a name="m_nwindowheight"></a>  CMFCTasksPaneTask::m_nWindowHeight

任务窗口的高度。 如果该任务有没有任务窗口，此值为零。

```
int m_nWindowHeight;
```

### <a name="remarks"></a>备注

##  <a name="m_pgroup"></a>  CMFCTasksPaneTask::m_pGroup

指向[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)所属此任务。

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>备注

每个任务必须具有父组。 您将组添加到任务窗格的通过调用[cmfctaskspane:: Addgroup](../../mfc/reference/cmfctaskspane-class.md#addgroup)。

##  <a name="m_rect"></a>  CMFCTasksPaneTask::m_rect

指定该任务的边界矩形。

```
CRect m_rect;
```

### <a name="remarks"></a>备注

绘制任务时，由框架计算此值。

##  <a name="m_strname"></a>  CMFCTasksPaneTask::m_strName

任务的名称。

```
CString m_strName;
```

### <a name="remarks"></a>备注

##  <a name="m_uicommandid"></a>  CMFCTasksPaneTask::m_uiCommandID

指定当用户单击该任务执行的命令的命令 ID。 如果此值不是有效的命令 ID，该任务视为一个简单的标签。

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>备注

##  <a name="setaccdata"></a>  CMFCTasksPaneTask::SetACCData

确定当前任务的可访问性数据。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*pParent*<br/>
[in]表示当前任务的父窗口。

*data*<br/>
[out]类型的对象`CAccessibilityData`填入当前任务的可访问性数据。

### <a name="return-value"></a>返回值

则为 TRUE*数据*参数已成功使用当前任务的可访问性数据填充; 否则为 FALSE。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)
