---
title: "CMFCTasksPaneTaskGroup 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 34bd53dec328ebf94e8bb9eb6f72aae1e8a90bc4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup 类
`CMFCTasksPaneTaskGroup`类是使用的帮助器类[CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)控件。 `CMFCTasksPaneTaskGroup` 类型的对象表示一个任务组 。 任务组是框架在具有折叠按钮的单独框中显示的项列表。 此框可具有一个可选标题（组名）。 如果一个组处于折叠状态，则任务列表不可见。  
  
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
  
|name|描述|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|确定是否将任务组对齐到任务窗格控件的底部。|  
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|确定任务组是否处于折叠状态。|  
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|确定任务组是否*特殊。* 框架显示特殊的标题以不同的颜色。|  
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|包含任务的内部列表。|  
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|指定组标题的边框。|  
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|指定组的边框。|  
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|指定组的名称。|  
  
## <a name="remarks"></a>备注  
 下图显示了展开的任务组：  
  
 ![展开的任务组](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
 下图显示了一个已折叠的任务组：  
  
 ![已折叠的任务组](../../mfc/reference/media/nexttaskgrpcollapse.png "nexttaskgrpcollapse")  
  
 下图显示无标题的任务组：  
  
 ![无标题的任务组](../../mfc/reference/media/nexttaskgrpnocapt.png "nexttaskgrpnocapt")  
  
 下图显示两个任务组。 第一个任务组设置标记为特殊`m_bIsSpecial`标志切换为`TRUE`，而第二个任务组并不特殊。 请注意，第一个任务组的标题是比第二个任务组暗：  
  
 ![特殊任务组](../../mfc/reference/media/nexttaskgrpspecial.png "nexttaskgrpspecial")  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxTasksPane.h  
  
##  <a name="cmfctaskspanetaskgroup"></a>CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup  
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
 `lpszName`  
 指定的组标题中的组的名称。  
  
 `bIsBottom`  
 指定是否将组对齐到任务窗格控件的底部。  
  
 `bIsSpecial`  
 指定是否将组指定为*特殊*因此，是否进行填充组标题与另一种颜色。  
  
 `bIsCollapsed`  
 指定组是否处于折叠状态。  
  
 `pPage`  
 指定此任务组所属的属性页。  
  
 `hIcon`  
 指定在组标题中显示的图标。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_bisbottom"></a>CMFCTasksPaneTaskGroup::m_bIsBottom  
 确定是否将任务组对齐到任务窗格控件的底部。  
  
```  
BOOL m_bIsBottom;  
```  
  
### <a name="remarks"></a>备注  
 只有一个组可以对齐到任务窗格控件的底部。 必须最后添加此任务组。 有关详细信息，请参阅[cmfctaskspane:: Addgroup](../../mfc/reference/cmfctaskspane-class.md#addgroup)。  
  
##  <a name="m_biscollapsed"></a>CMFCTasksPaneTaskGroup::m_bIsCollapsed  
 确定任务组是否处于折叠状态。  
  
```  
BOOL m_bIsCollapsed;  
```  
  
### <a name="remarks"></a>备注  
 你可以启用或禁用折叠的任务窗格上的组，通过调用的能力[cmfctaskspane:: Enablegroupcollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse)。  
  
##  <a name="m_bisspecial"></a>CMFCTasksPaneTaskGroup::m_bIsSpecial  
 确定任务组是否*特殊*和是否为特殊任务组标题应由另一种颜色。  
  
```  
BOOL m_bIsSpecial;  
```  
  
### <a name="remarks"></a>备注  
 如果你的应用程序正在使用 Windows XP 可视主题和`m_bIsSpecial`是`FALSE`，框架调用`DrawThemeBackground`与`EBP_NORMALGROUPBACKGROUND`标志。 如果`m_bIsSpecial`是`TRUE`，框架调用`DrawThemeBackground`与`EBP_SPECIALGROUPBACKGROUND`标志。  
  
##  <a name="m_lsttasks"></a>CMFCTasksPaneTaskGroup::m_lstTasks  
 包含任务的内部列表。  
  
```  
CObList m_lstTasks;  
```  
  
### <a name="remarks"></a>备注  
 若要填充此列表，调用[cmfctaskspane:: Addtask](../../mfc/reference/cmfctaskspane-class.md#addtask)。  
  
##  <a name="m_rect"></a>CMFCTasksPaneTaskGroup::m_rect  
 指定组标题的边框。  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>备注  
 此值将由框架自动计算。  
  
##  <a name="m_rectgroup"></a>CMFCTasksPaneTaskGroup::m_rectGroup  
 指定组的边框。  
  
```  
CRect m_rectGroup;  
```  
  
### <a name="remarks"></a>备注  
 此值将由框架自动计算。  
  
##  <a name="m_strname"></a>CMFCTasksPaneTaskGroup::m_strName  
 指定组的名称。  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>备注  
 如果此值为空，不显示组标题，并且无法折叠组。  
  
##  <a name="setaccdata"></a>CMFCTasksPaneTaskGroup::SetACCData  
 确定当前的任务组的可访问性数据。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParent`  
 表示当前的任务组的父窗口。  
  
 [out] `data`  
 类型的对象`CAccessibilityData`并且填充了当前的任务组的可访问性数据。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`data`参数已成功填充了当前的任务组的可访问性数据; 否则为`FALSE`。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCTasksPane 类](../../mfc/reference/cmfctaskspane-class.md)   
 [CMFCTasksPaneTask 类](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)
