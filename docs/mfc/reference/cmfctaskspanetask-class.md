---
title: CMFCTasksPaneTask 类 |Microsoft 文档
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
ms.openlocfilehash: 4008389121a1a78ca746798af7f3fc18c9663b93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cmfctaskspanetask-class"></a>CMFCTasksPaneTask 类
`CMFCTasksPaneTask`类是一个帮助器类，表示任务窗格控件任务的 ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md))。 任务对象表示任务组中的项 ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md))。 每个任务可具有在用户单击任务和显示在任务名称左侧的图标时框架所执行的命令。  
  
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
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|确定当前的任务的可访问性数据。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|确定是否自动销毁任务窗口。|  
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|确定是否框架在绘制任务标签中显示为粗体文本。|  
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|包含框架将与任务相关联的用户定义的数据。 如果该任务没有关联的数据，则设置为零。|  
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|任务窗口的句柄。|  
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|框架任务旁边显示的图像的图像列表中的索引。|  
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|任务窗口的高度。 如果任务具有未任务窗口，此值为零。|  
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|指向的指针`CMFCTasksPaneTaskGroup`属于此任务。|  
|[CMFCTasksPaneTask::m_rect](#m_rect)|指定任务的边框。|  
|[CMFCTasksPaneTask::m_strName](#m_strname)|任务的名称。|  
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|指定用户单击任务时框架所执行的命令的命令 ID。 如果此值不是有效的命令 ID，该任务将被视为一个简单的标签。|  
  
## <a name="remarks"></a>备注  
 下图显示一个包含三个任务的任务组：  
  
 ![展开的任务组](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
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
 `pGroup`  
 指定[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)任务所属。  
  
 `lpszName`  
 指定任务的名称。  
  
 `nIcon`  
 图像列表中指定该任务的映像的索引。  
  
 `uiCommandID`  
 指定当任务被单击时执行的命令的命令 ID。  
  
 `dwUserData`  
 用户定义的数据。  
  
 `hwndTask`  
 指定任务窗口的句柄。  
  
 `bAutoDestroyWindow`  
 如果`TRUE`，任务窗口将自动销毁。  
  
 `nWindowHeight`  
 指定的任务窗口的高度。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_bautodestroywindow"></a>  CMFCTasksPaneTask::m_bAutoDestroyWindow  
 确定是否自动销毁任务窗口。  
  
```  
BOOL m_bAutoDestroyWindow;  
```  
  
### <a name="remarks"></a>备注  
 设置为`TRUE`可指定任务窗口 ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) 自动; 否则为应销毁`FALSE`。  
  
##  <a name="m_bisbold"></a>  CMFCTasksPaneTask::m_bIsBold  
 确定是否将任务标签绘制粗体文本。  
  
```  
BOOL m_bIsBold;  
```  
  
### <a name="remarks"></a>备注  
 此成员设置为`TRUE`以显示任务标签显示为粗体文本。  
  
##  <a name="m_dwuserdata"></a>  CMFCTasksPaneTask::m_dwUserData  
 包含与任务关联的用户定义的数据。 如果数据不会与任务关联，则设置为零。  
  
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
 若要添加的任务窗口，调用[CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow)。  
  
##  <a name="m_nicon"></a>  CMFCTasksPaneTask::m_nIcon  
 标识指定的任务旁边显示的图像的图像列表中的索引位置。  
  
```  
int m_nIcon;  
```  
  
### <a name="remarks"></a>备注  
 图像列表将由[CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist)。  
  
 设置`m_nIcon`为-1，如果你想要显示的任务，如果没有图像。  
  
##  <a name="m_nwindowheight"></a>  CMFCTasksPaneTask::m_nWindowHeight  
 任务窗口的高度。 如果任务具有未任务窗口，此值为零。  
  
```  
int m_nWindowHeight;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_pgroup"></a>  CMFCTasksPaneTask::m_pGroup  
 指向[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)此任务所属。  
  
```  
CMFCTasksPaneTaskGroup* m_pGroup;  
```  
  
### <a name="remarks"></a>备注  
 每个任务必须具有父组。 你将组添加到任务窗格的通过调用[cmfctaskspane:: Addgroup](../../mfc/reference/cmfctaskspane-class.md#addgroup)。  
  
##  <a name="m_rect"></a>  CMFCTasksPaneTask::m_rect  
 指定任务的边框。  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>备注  
 绘制任务时，将由框架计算此值。  
  
##  <a name="m_strname"></a>  CMFCTasksPaneTask::m_strName  
 任务的名称。  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_uicommandid"></a>  CMFCTasksPaneTask::m_uiCommandID  
 指定当用户单击该任务执行的命令的命令 ID。 如果此值不是有效的命令 ID，该任务将被视为一个简单的标签。  
  
```  
UINT m_uiCommandID;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="setaccdata"></a>  CMFCTasksPaneTask::SetACCData  
 确定当前的任务的可访问性数据。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParent`  
 表示当前任务的父窗口。  
  
 [out] `data`  
 类型的对象`CAccessibilityData`填充当前任务可访问性数据。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果`data`参数已成功填充了当前任务可访问性数据; 否则为`FALSE`。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)
