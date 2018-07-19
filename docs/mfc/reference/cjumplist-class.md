---
title: CJumpList 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CJumpList
- AFXADV/CJumpList
- AFXADV/CJumpList::CJumpList
- AFXADV/CJumpList::AbortList
- AFXADV/CJumpList::AddDestination
- AFXADV/CJumpList::AddKnownCategory
- AFXADV/CJumpList::AddTask
- AFXADV/CJumpList::AddTasks
- AFXADV/CJumpList::AddTaskSeparator
- AFXADV/CJumpList::ClearAll
- AFXADV/CJumpList::ClearAllDestinations
- AFXADV/CJumpList::CommitList
- AFXADV/CJumpList::GetDestinationList
- AFXADV/CJumpList::GetMaxSlots
- AFXADV/CJumpList::GetRemovedItems
- AFXADV/CJumpList::InitializeList
- AFXADV/CJumpList::SetAppID
dev_langs:
- C++
helpviewer_keywords:
- CJumpList [MFC], CJumpList
- CJumpList [MFC], AbortList
- CJumpList [MFC], AddDestination
- CJumpList [MFC], AddKnownCategory
- CJumpList [MFC], AddTask
- CJumpList [MFC], AddTasks
- CJumpList [MFC], AddTaskSeparator
- CJumpList [MFC], ClearAll
- CJumpList [MFC], ClearAllDestinations
- CJumpList [MFC], CommitList
- CJumpList [MFC], GetDestinationList
- CJumpList [MFC], GetMaxSlots
- CJumpList [MFC], GetRemovedItems
- CJumpList [MFC], InitializeList
- CJumpList [MFC], SetAppID
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c4090ebfa432f1d8b7f05942a6b1af68b75d270
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337887"
---
# <a name="cjumplist-class"></a>CJumpList 类
一个`CJumpList`是右键单击任务栏中的图标时显示的快捷方式列表。  
  
## <a name="syntax"></a>语法  
  
```  
class CJumpList;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CJumpList::CJumpList](#cjumplist)|构造 `CJumpList` 对象。|  
|[CJumpList:: ~ CJumpList](#cjumplist__~cjumplist)|销毁 `CJumpList` 对象。|  
  
|name|描述|  
|----------|-----------------|  
|[CJumpList::AbortList](#abortlist)|无需处理将中止生成列表的事务。|  
|[CJumpList::AddDestination](#adddestination)|已重载。 将目标添加到列表。|  
|[CJumpList::AddKnownCategory](#addknowncategory)|将已知类别追加到列表。|  
|[CJumpList::AddTask](#addtask)|已重载。 将项添加到规范的任务类别。|  
|[CJumpList::AddTasks](#addtasks)|将项添加到规范的任务类别。|  
|[CJumpList::AddTaskSeparator](#addtaskseparator)|添加任务之间的分隔符。|  
|[CJumpList::ClearAll](#clearall)|删除所有任务和已添加到的当前实例的目标`CJumpList`到目前为止。|  
|[CJumpList::ClearAllDestinations](#clearalldestinations)|删除已添加到的当前实例的所有目标`CJumpList`到目前为止。|  
|[CJumpList::CommitList](#commitlist)|结束生成列表的事务并将报告的列表提交到相关联的存储 （在此情况下注册表。）|  
|[CJumpList::GetDestinationList](#getdestinationlist)|检索到目标列表的接口指针。|  
|[CJumpList::GetMaxSlots](#getmaxslots)|检索项，包括可以在调用应用程序的目标菜单中显示的类别标题的最大数目。|  
|[CJumpList::GetRemovedItems](#getremoveditems)|返回表示项的数组中删除目标。|  
|[CJumpList::InitializeList](#initializelist)|开始一个生成列表的事务。|  
|[CJumpList::SetAppID](#setappid)|设置应用程序用户模型 ID，将生成的列表。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CJumpList](../../mfc/reference/cjumplist-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxadv.h  
  
##  <a name="_dtorcjumplist"></a>  CJumpList:: ~ CJumpList  
 销毁 `CJumpList` 对象。  
  
```  
~CJumpList();
```  
  
##  <a name="abortlist"></a>  CJumpList::AbortList  
 无需处理将中止生成列表的事务。  
  
```  
void AbortList();
```  
  
### <a name="remarks"></a>备注  
 调用此方法不会有相同的效果销毁`CJumpList`而无需调用`CommitList`。  
  
##  <a name="adddestination"></a>  CJumpList::AddDestination  
 将目标添加到列表。  
  
```  
BOOL AddDestination(
    LPCTSTR lpcszCategoryName,  
    LPCTSTR strDestinationPath);

 
BOOL AddDestination(
    LPCTSTR strCategoryName,  
    IShellItem* pShellItem);

 
BOOL AddDestination(
    LPCTSTR strCategoryName,  
    IShellLink* pShellLink);
```  
  
### <a name="parameters"></a>参数  
 *lpcszCategoryName*  
 指定的类别名称。 如果指定的类别不存在，将创建它。  
  
 *strDestinationPath*  
 指定目标文件的路径。  
  
 *strCategoryName*  
 指定的类别名称。 如果指定的类别不存在，将创建它。  
  
 *pShellItem*  
 指定表示要添加的目标的 Shell 项。  
  
 *pShellLink*  
 指定表示要添加的目标的命令行程序链接。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 实例`CJumpList`在内部累积添加了的目标，然后提交事务，在`CommitList`。  
  
##  <a name="addknowncategory"></a>  CJumpList::AddKnownCategory  
 将已知类别追加到列表。  
  
```  
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```  
  
### <a name="parameters"></a>参数  
 *category*  
 指定已知的类别类型。 可以是 KDC_RECENT 或 KDC_KNOWN。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 已知类别是我们将自动计算每个应用程序使用的常见和最近类别`SHAddToRecentDocs`（或间接使用它，如命令行程序将在某些情况下的应用程序的名义调用它）。  
  
##  <a name="addtask"></a>  CJumpList::AddTask  
 将项添加到规范的任务类别。  
  
```  
BOOL AddTask(
    LPCTSTR strTargetExecutablePath,  
    LPCTSTR strCommandLineArgs,  
    LPCTSTR strTitle,  
    LPCTSTR strIconLocation,  
    int iIconIndex);  
  
BOOL AddTask(IShellLink* pShellLink);
```  
  
### <a name="parameters"></a>参数  
 *strTargetExecutablePath*  
 指定目标任务路径。  
  
 *strCommandLineArgs*  
 指定由 strTargetExecutablePath 指定的可执行文件的命令行参数。  
  
 *strTitle*  
 将在目标列表中显示的任务名称。  
  
 *strIconLocation*  
 将和标题的目标列表中显示的图标的位置。  
  
 *iIconIndex*  
 图标的索引。  
  
 *pShellLink*  
 表示要添加的任务的命令行程序链接。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 实例`CJumpList`累积指定的任务并将它们添加到的目标列表期间`CommitList`。 任务项将出现在应用程序的目标菜单底部的类别。 在填充 UI 中时，此类别优先于所有其他类别。  
  
##  <a name="addtasks"></a>  CJumpList::AddTasks  
 将项添加到规范的任务类别。  
  
```  
BOOL AddTasks(IObjectArray* pObjectCollection);
```  
  
### <a name="parameters"></a>参数  
 *pObjectCollection*  
 要添加的任务的集合。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 CJumpList 实例累积指定的任务，并将它们添加到的目标列表期间`CommitList`。 任务项将出现在应用程序的目标菜单底部的类别。 在填充 UI 中时，此类别优先于所有其他类别。  
  
##  <a name="addtaskseparator"></a>  CJumpList::AddTaskSeparator  
 添加任务之间的分隔符。  
  
```  
BOOL AddTaskSeparator();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，如果不是 0。  
  
##  <a name="cjumplist"></a>  CJumpList::CJumpList  
 构造 `CJumpList` 对象。  
  
```  
CJumpList(BOOL bAutoCommit = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bAutoCommit*  
 如果此参数为 FALSE 后不析构函数中自动提交列表。  
  
##  <a name="clearall"></a>  CJumpList::ClearAll  
 删除所有任务和已添加到的当前实例的目标`CJumpList`到目前为止。  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>备注  
 此方法清除并释放所有数据和内部接口。  
  
##  <a name="clearalldestinations"></a>  CJumpList::ClearAllDestinations  
 删除已添加到当前实例的 CJumpList 到目前为止的所有目标。  
  
```  
void ClearAllDestinations();
```  
  
### <a name="remarks"></a>备注  
 如果你需要删除所有目的地的目标列表构建在当前会话中添加了到目前为止，再次添加其他目标，请调用此函数。 如果内部`ICustomDestinationList`已初始化，它处于活动状态。  
  
##  <a name="commitlist"></a>  CJumpList::CommitList  
 结束生成列表的事务并提交到相关联的存储 （在此情况下注册表） 的报告的列表。  
  
```  
BOOL CommitList();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 提交是原子的。 如果提交失败，则将返回错误。  当`CommitList`调用时，当前将清理已删除的项的列表。 调用此方法会重置该对象，以便它不具有活动的列表生成的事务。 若要更新的列表，`BeginList`需要再次调用。  
  
##  <a name="getdestinationlist"></a>  CJumpList::GetDestinationList  
 检索到目标列表的接口指针。  
  
```  
ICustomDestinationList* GetDestinationList();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 如果跳转列表尚未初始化，或已提交或中止，则返回的值将为 NULL。  
  
##  <a name="getmaxslots"></a>  CJumpList::GetMaxSlots  
 检索项，包括可以在调用应用程序的目标菜单中显示的类别标题的最大数目。  
  
```  
UINT GetMaxSlots() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 应用程序可能仅会报告项数和类别组合直到达到此值的标头。 如果调用`AppendCategory`， `AppendKnownCategory`，或`AddUserTasks`超过此数字，它们将返回失败。  
  
##  <a name="getremoveditems"></a>  CJumpList::GetRemovedItems  
 返回表示项的数组中删除目标。  
  
```  
IObjectArray* GetRemovedItems();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 跳转列表的初始化过程中检索已删除的目标。 在生成新的目标列表时，应用程序应首先处理已删除的目标列表中，清除已删除的列表枚举器返回任何项及其跟踪数据。 如果应用程序尝试提供只是已在当前调用对事务中删除的项`BeginList`启动，重新添加该项目的方法调用将失败，以确保应用程序所遵循的已删除的列表。  
  
##  <a name="initializelist"></a>  CJumpList::InitializeList  
 开始一个生成列表的事务。  
  
```  
BOOL InitializeList();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 无需显式调用此方法，除非你想要检索一个指向`ICustomDestinationList`使用`GetDestinationList`，可使用的槽数`GetMaxSlots`，或使用已删除项的列表`GetRemovedItems`。  
  
##  <a name="setappid"></a>  CJumpList::SetAppID  
 设置应用程序用户模型 ID，将生成的列表。  
  
```  
void SetAppID(LPCTSTR strAppID);
```  
  
### <a name="parameters"></a>参数  
 *strAppID*  
 一个字符串，指定应用程序用户模型 id。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
