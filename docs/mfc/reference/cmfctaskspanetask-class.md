---
title: CMFC任务窗格任务类
ms.date: 11/19/2018
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
ms.openlocfilehash: 49fccdf161da7deb1fd88a12a107df40bafdae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375870"
---
# <a name="cmfctaskspanetask-class"></a>CMFC任务窗格任务类

类`CMFCTasksPaneTask`是一个帮助器类，表示任务窗格控件的任务 （ [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)）。 任务对象表示任务组中的项[（CMFC任务窗格任务组](../../mfc/reference/cmfctaskspanetaskgroup-class.md)）。 每个任务可具有在用户单击任务和显示在任务名称左侧的图标时框架所执行的命令。

## <a name="syntax"></a>语法

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC任务窗格任务：：CMFC任务窗格任务](#cmfctaskspanetask)|创建并初始化一个 `CMFCTasksPaneTask` 对象。|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC任务窗格任务：：设置ACC数据](#setaccdata)|确定当前任务的辅助功能数据。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFC任务窗格任务：：m_bAutoDestroyWindow](#m_bautodestroywindow)|确定任务窗口是否自动销毁。|
|[CMFC任务窗格任务：：m_bIsBold](#m_bisbold)|确定框架是否以粗体文本绘制任务标签。|
|[CMFC任务窗格任务：：m_dwUserData](#m_dwuserdata)|包含框架与任务关联的用户定义数据。 如果任务没有关联的数据，则设置为零。|
|[CMFC任务窗格任务：：m_hwndTask](#m_hwndtask)|任务窗口的句柄。|
|[CMFC任务窗格任务：：m_nIcon](#m_nicon)|框架显示在任务旁边的图像图像列表中的索引。|
|[CMFC任务窗格任务：：m_nWindowHeight](#m_nwindowheight)|任务窗口的高度。 如果任务没有任务窗口，则此值为零。|
|[CMFC任务窗格任务：：m_pGroup](#m_pgroup)|指向此任务所属`CMFCTasksPaneTaskGroup`的 的指针。|
|[CMFC任务窗格任务：：m_rect](#m_rect)|指定任务的边界矩形。|
|[CMFC任务窗格任务：：m_strName](#m_strname)|任务的名称。|
|[CMFC任务窗格任务：：m_uiCommandID](#m_uicommandid)|指定框架在用户单击任务时执行的命令的命令 ID。 如果此值不是有效的命令 ID，则任务将被视为简单标签。|

## <a name="remarks"></a>备注

下图显示了包含三个任务的任务组：

![已展开的任务组](../../mfc/reference/media/nexttaskgrpexpand.png "已展开的任务组")

> [!NOTE]
> 如果任务没有有效的命令 ID，则将其视为简单标签。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>要求

**标题：** afxTasksPane.h

## <a name="cmfctaskspanetaskcmfctaskspanetask"></a><a name="cmfctaskspanetask"></a>CMFC任务窗格任务：：CMFC任务窗格任务

创建并初始化一个 `CMFCTasksPaneTask` 对象。

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

*p组*<br/>
指定任务所属的[CMFC 任务窗格任务组](../../mfc/reference/cmfctaskspanetaskgroup-class.md)。

*lpsz名称*<br/>
指定任务的名称。

*nIcon*<br/>
在图像列表中指定任务图像的索引。

*uiCommandID*<br/>
指定单击任务时执行的命令的命令 ID。

*dwUserData*<br/>
用户定义的数据。

*hwndTask*<br/>
指定任务窗口的句柄。

*b 自动销毁窗口*<br/>
如果为 TRUE，则任务窗口将自动销毁。

*n 窗口高度*<br/>
指定任务窗口的高度。

### <a name="remarks"></a>备注

## <a name="cmfctaskspanetaskm_bautodestroywindow"></a><a name="m_bautodestroywindow"></a>CMFC任务窗格任务：：m_bAutoDestroyWindow

确定任务窗口是否自动销毁。

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>备注

设置为 TRUE 以指定应自动销毁任务窗口[（CMFC任务窗格任务：：：m_hwndTask](#m_hwndtask)）;否则，FALSE。

## <a name="cmfctaskspanetaskm_bisbold"></a><a name="m_bisbold"></a>CMFC任务窗格任务：：m_bIsBold

确定是否以粗体文本绘制任务标签。

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>备注

将此成员设置为 TRUE 以显示任务标签的粗体文本。

## <a name="cmfctaskspanetaskm_dwuserdata"></a><a name="m_dwuserdata"></a>CMFC任务窗格任务：：m_dwUserData

包含与任务关联的用户定义的数据。 如果没有数据与任务关联，则设置为零。

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>备注

## <a name="cmfctaskspanetaskm_hwndtask"></a><a name="m_hwndtask"></a>CMFC任务窗格任务：：m_hwndTask

任务窗口的句柄。

```
HWND m_hwndTask;
```

### <a name="remarks"></a>备注

要添加任务窗口，请致电[CMFC任务窗格：：添加窗口](../../mfc/reference/cmfctaskspane-class.md#addwindow)。

## <a name="cmfctaskspanetaskm_nicon"></a><a name="m_nicon"></a>CMFC任务窗格任务：：m_nIcon

图像列表中的索引位置，用于标识显示在指定任务旁边的图像。

```
int m_nIcon;
```

### <a name="remarks"></a>备注

映像列表由[CMFC 任务窗格设置：：设置图标列表](../../mfc/reference/cmfctaskspane-class.md#seticonslist)。

如果要`m_nIcon`在没有图像的情况下显示任务，则设置为 -1。

## <a name="cmfctaskspanetaskm_nwindowheight"></a><a name="m_nwindowheight"></a>CMFC任务窗格任务：：m_nWindowHeight

任务窗口的高度。 如果任务没有任务窗口，则此值为零。

```
int m_nWindowHeight;
```

### <a name="remarks"></a>备注

## <a name="cmfctaskspanetaskm_pgroup"></a><a name="m_pgroup"></a>CMFC任务窗格任务：：m_pGroup

指向此任务所属的[CMFC 任务PaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)的指针。

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>备注

每个任务都必须有一个父组。 通过调用[CMFC任务窗格：：添加组](../../mfc/reference/cmfctaskspane-class.md#addgroup)，将组添加到任务窗格中。

## <a name="cmfctaskspanetaskm_rect"></a><a name="m_rect"></a>CMFC任务窗格任务：：m_rect

指定任务的边界矩形。

```
CRect m_rect;
```

### <a name="remarks"></a>备注

绘制任务时，由框架计算此值。

## <a name="cmfctaskspanetaskm_strname"></a><a name="m_strname"></a>CMFC任务窗格任务：：m_strName

任务的名称。

```
CString m_strName;
```

### <a name="remarks"></a>备注

## <a name="cmfctaskspanetaskm_uicommandid"></a><a name="m_uicommandid"></a>CMFC任务窗格任务：：m_uiCommandID

指定用户单击任务时执行的命令的命令 ID。 如果此值不是有效的命令 ID，则任务将被视为简单标签。

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>备注

## <a name="cmfctaskspanetasksetaccdata"></a><a name="setaccdata"></a>CMFC任务窗格任务：：设置ACC数据

确定当前任务的辅助功能数据。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*p 父级*<br/>
[在]表示当前任务的父窗口。

*数据*<br/>
[出]使用当前任务的辅助`CAccessibilityData`数据填充的类型对象。

### <a name="return-value"></a>返回值

如果*数据*参数已成功填充当前任务的辅助功能数据，则为 TRUE;否则，FALSE。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)
