---
title: "CUserToolsManager 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CreateNewTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::FindTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetArgumentsMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetFilter
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetInitialDirMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetMaxTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetToolsEntryCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetUserTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::InvokeTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::IsUserToolCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::LoadState
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolDown
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolUp
- AFXUSERTOOLSMANAGER/CUserToolsManager::RemoveTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::SaveState
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetFilter
dev_langs:
- C++
helpviewer_keywords:
- CUserToolsManager class
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0b82adf0f9eba5ee334ada2c169546f27894c1dd
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager 类
集合进行维护[CUserTool 类](../../mfc/reference/cusertool-class.md)应用程序中的对象。 用户工具是运行外部应用程序的菜单项。 `CUserToolsManager` 对象使用户或开发人员能够将新的用户工具添加到应用程序中。 它支持与用户工具关联的命令的执行，并将与用户工具相关的信息保存到 Windows 注册表中。  
  
## <a name="syntax"></a>语法  
  
```  
class CUserToolsManager : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|构造一个 `CUserToolsManager`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CUserToolsManager::CreateNewTool](#createnewtool)|创建一个新的用户工具。|  
|[CUserToolsManager::FindTool](#findtool)|返回指向`CMFCUserTool`与指定的命令 ID 相关联的对象|  
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|返回与关联的资源 ID**参数**上的菜单**工具**的选项卡上**自定义**对话框。|  
|[CUserToolsManager::GetDefExt](#getdefext)|返回的默认扩展名**文件打开**对话框中 ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) 中使用**命令**字段**工具**的选项卡上**自定义**对话框。|  
|[CUserToolsManager::GetFilter](#getfilter)|返回文件筛选器**文件打开**对话框中 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**的选项卡上**自定义**对话框。|  
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|返回与关联的资源 ID**初始目录**上的菜单**工具**的选项卡上**自定义**对话框。|  
|[CUserToolsManager::GetMaxTools](#getmaxtools)|应用程序中返回的最大可分配的用户工具数。|  
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|返回用户工具的菜单项占位符的命令 ID。|  
|[CUserToolsManager::GetUserTools](#getusertools)|返回到的用户工具列表的引用。|  
|[CUserToolsManager::InvokeTool](#invoketool)|执行具有指定的命令 id。 该用户工具关联的应用程序|  
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|确定命令 ID 是否与用户工具相关联。|  
|[CUserToolsManager::LoadState](#loadstate)|从 Windows 注册表中加载与用户工具的信息。|  
|[CUserToolsManager::MoveToolDown](#movetooldown)|用户工具列表中下移指定的用户工具。|  
|[CUserToolsManager::MoveToolUp](#movetoolup)|用户工具列表中上移指定的用户工具。|  
|[CUserToolsManager::RemoveTool](#removetool)|从应用程序中移除指定的用户工具。|  
|[CUserToolsManager::SaveState](#savestate)|在 Windows 注册表中存储有关用户工具的信息。|  
|[CUserToolsManager::SetDefExt](#setdefext)|指定默认扩展插件，**文件打开**对话框中 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**的选项卡上**自定义**对话框。|  
|[CUserToolsManager::SetFilter](#setfilter)|指定该文件筛选**文件打开**对话框中 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**的选项卡上**自定义**对话框。|  
  
## <a name="remarks"></a>备注  
 若要将用户工具合并到您的应用程序，您必须︰  
  
 1. 保留一个菜单项和工具的一个用户菜单项关联的命令 ID。  
  
 2. 保留每个用户工具，用户可以在您的应用程序中定义的顺序的命令 ID。  
  
 3. 调用[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)方法并提供以下参数︰ 菜单命令 ID、 第一个用户工具命令 ID 和最后一个用户工具的命令 id。  
  
 应该只有一个全局`CUserToolsManager`每个应用程序的对象。  
  
 用户工具的示例，请参阅 VisualStudioDemo 示例项目。  
  
## <a name="example"></a>示例  
 下面的示例演示如何检索对引用`CUserToolsManager`对象以及如何创建新的用户工具。 此代码段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&38;](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CUserToolsManager`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxusertoolsmanager.h  
  
##  <a name="createnewtool"></a>CUserToolsManager::CreateNewTool  
 创建一个新的用户工具。  
  
```  
CUserTool* CreateNewTool();
```  
  
### <a name="return-value"></a>返回值  
 指向新创建的用户工具，或`NULL`的用户工具数是否超过了最大值。 返回的类型是传递到的类型相同`CWinAppEx::EnableUserTools`作为`pToolRTC`参数。  
  
### <a name="remarks"></a>备注  
 此方法的调用中提供的范围内找到的第一个可用的菜单命令 ID [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) ，并将用户工具分配此 id。  
  
 如果工具的数目已达到最大值，该方法将失败。 在范围内的所有命令 Id 都分配到用户工具时，将发生这种情况。 可以通过调用检索的最大工具数[CUserToolsManager::GetMaxTools](#getmaxtools)。 您可以通过调用有权访问的工具列表[CUserToolsManager::GetUserTools](#getusertools)方法。  
  
##  <a name="cusertoolsmanager"></a>CUserToolsManager::CUserToolsManager  
 构造一个 `CUserToolsManager`。 每个应用程序必须具有最多个用户工具管理器。  
  
```  
CUserToolsManager();

 
CUserToolsManager(
    const UINT uiCmdToolsDummy,  
    const UINT uiCmdFirst,  
    const UINT uiCmdLast,  
    CRuntimeClass* pToolRTC=RUNTIME_CLASS(CUserTool),  
    UINT uArgMenuID=0,  
    UINT uInitDirMenuID=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdToolsDummy`  
 无符号的整数，该框架作为占位符用于用户的工具菜单的命令 ID。  
  
 [in] `uiCmdFirst`  
 第一个用户工具命令的命令 ID。  
  
 [in] `uiCmdLast`  
 最后一个用户工具命令的命令 ID。  
  
 [in] `pToolRTC`  
 类的[CUserToolsManager::CreateNewTool](#createnewtool)创建。 通过使用此类，您可以使用的派生的类型[CUserTool 类](../../mfc/reference/cusertool-class.md)而不是默认实现。  
  
 [in] `uArgMenuID`  
 参数弹出菜单的菜单资源 ID。  
  
 [in] `uInitDirMenuID`  
 初始目录弹出菜单的菜单资源 ID。  
  
### <a name="remarks"></a>备注  
 请勿调用此构造函数。 而应调用[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)为启用的用户工具，并调用[CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager)若要获取的指针`CUserToolsManager`。 有关详细信息，请参阅[用户定义的工具](../../mfc/user-defined-tools.md)。  
  
##  <a name="findtool"></a>CUserToolsManager::FindTool  
 返回指向[CUserTool 类](../../mfc/reference/cusertool-class.md)与指定的命令 ID 相关联的对象  
  
```  
CUserTool* FindTool(UINT uiCmdId) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdId`  
 菜单命令标识符。  
  
### <a name="return-value"></a>返回值  
 一个指向[CUserTool 类](../../mfc/reference/cusertool-class.md)或`CUserTool`-如果派生的对象成功; 否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 当`FindTool`是成功，则返回的类型为的类型相同`pToolRTC`参数[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。  
  
##  <a name="getargumentsmenuid"></a>CUserToolsManager::GetArgumentsMenuID  
 返回与关联的资源 ID**参数**上的菜单**工具**的选项卡上**自定义**对话框。  
  
```  
UINT GetArgumentsMenuID() const;  
```  
  
### <a name="return-value"></a>返回值  
 菜单资源的标识符。  
  
### <a name="remarks"></a>备注  
 `uArgMenuID`参数[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)指定的资源 ID。  
  
##  <a name="getdefext"></a>CUserToolsManager::GetDefExt  
 返回的默认扩展名**文件打开**对话框中 ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) 中使用**命令**字段**工具**的选项卡上**自定义**对话框。  
  
```  
const CString& GetDefExt() const;  
```  
  
### <a name="return-value"></a>返回值  
 对引用`CString`包含扩展的对象。  
  
##  <a name="getfilter"></a>CUserToolsManager::GetFilter  
 返回文件筛选器**文件打开**对话框中 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**的选项卡上**自定义**对话框。  
  
```  
const CString& GetFilter() const;  
```  
  
### <a name="return-value"></a>返回值  
 对引用`CString`包含的筛选器的对象。  
  
##  <a name="getinitialdirmenuid"></a>CUserToolsManager::GetInitialDirMenuID  
 返回与关联的资源 ID**初始目录**上的菜单**工具**的选项卡上**自定义**对话框。  
  
```  
UINT GetInitialDirMenuID() const;  
```  
  
### <a name="return-value"></a>返回值  
 菜单资源标识符。  
  
### <a name="remarks"></a>备注  
 返回的 ID 指定在`uInitDirMenuID`参数[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。  
  
##  <a name="getmaxtools"></a>CUserToolsManager::GetMaxTools  
 应用程序中返回的最大可分配的用户工具数。  
  
```  
int GetMaxTools() const;  
```  
  
### <a name="return-value"></a>返回值  
 最大可分配的用户工具数。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索的最大可分配应用程序中的工具数。 此数字是从范围中的 Id 数`uiCmdFirst`通过`uiCmdLast`参数传递给[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。  
  
##  <a name="gettoolsentrycmd"></a>CUserToolsManager::GetToolsEntryCmd  
 返回用户工具的菜单项占位符的命令 ID。  
  
```  
UINT GetToolsEntryCmd() const;  
```  
  
### <a name="return-value"></a>返回值  
 占位符的命令 ID。  
  
### <a name="remarks"></a>备注  
 若要启用用户工具，请调用[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。 `uiCmdToolsDummy`参数指定工具条目命令的命令 ID。 此方法返回工具项的命令 id。 在菜单中使用该 ID，无论它时被替换的用户工具列表将显示的菜单。  
  
##  <a name="getusertools"></a>CUserToolsManager::GetUserTools  
 返回到的用户工具列表的引用。  
  
```  
const CObList& GetUserTools() const;  
```  
  
### <a name="return-value"></a>返回值  
 常量引用[CObList 类](../../mfc/reference/coblist-class.md)对象，其中包含的用户工具列表。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索用户的列表工具[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)对象维护。 由类型的对象表示每个用户工具[CUserTool 类](../../mfc/reference/cusertool-class.md)或一种类型派生自`CUserTool`。 指定的类型`pToolRTC`参数在调用时[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)以启用用户工具。  
  
##  <a name="invoketool"></a>CUserToolsManager::InvokeTool  
 执行具有指定的命令 id。 该用户工具关联的应用程序  
  
```  
BOOL InvokeTool(UINT uiCmdId);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdId`  
 与用户工具关联的菜单命令 ID。  
  
### <a name="return-value"></a>返回值  
 如果与用户工具关联的命令执行成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此方法以执行与用户关联的应用程序工具具有由指定的命令 ID `uiCmdId`。  
  
##  <a name="isusertoolcmd"></a>CUserToolsManager::IsUserToolCmd  
 确定命令 ID 是否与用户工具相关联。  
  
```  
BOOL IsUserToolCmd(UINT uiCmdId) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdId`  
 菜单项的命令 ID。  
  
### <a name="return-value"></a>返回值  
 如果给定的命令 ID 的用户工具; 与相关联，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法检查命令 ID 范围中是否为给定的命令 ID。 在调用时指定的范围[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)以启用用户工具。  
  
##  <a name="loadstate"></a>CUserToolsManager::LoadState  
 从 Windows 注册表中加载与用户工具的信息。  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 Windows 注册表项的路径。  
  
### <a name="return-value"></a>返回值  
 如果状态加载成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法加载的状态`CUserToolsManager`Windows 注册表中的对象。  
  
 通常情况下，您不直接调用此方法。 [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)调用其作为工作区初始化过程的一部分。  
  
##  <a name="movetooldown"></a>CUserToolsManager::MoveToolDown  
 用户工具列表中下移指定的用户工具。  
  
```  
BOOL MoveToolDown(CUserTool* pTool);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTool`  
 指定要移动的用户工具。  
  
### <a name="return-value"></a>返回值  
 如果成功，则向下移动用户工具，非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果此方法失败该工具，`pTool`指定不在内部的列表或如果该工具已在列表中最后一个。  
  
##  <a name="movetoolup"></a>CUserToolsManager::MoveToolUp  
 用户工具列表中上移指定的用户工具。  
  
```  
BOOL MoveToolUp(CUserTool* pTool);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTool`  
 指定要移动的用户工具。  
  
### <a name="return-value"></a>返回值  
 如果成功，则向上移动用户工具，非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果此方法失败该工具，`pTool`参数指定不在内部的列表或如果该工具已在列表中的第一个工具项。  
  
##  <a name="removetool"></a>CUserToolsManager::RemoveTool  
 从应用程序中移除指定的用户工具。  
  
```  
BOOL RemoveTool(CUserTool* pTool);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pTool`  
 一个指向要删除的用户工具。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功移除了该工具。 否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 如果成功移除了该工具，则此方法删除`pTool`。  
  
##  <a name="savestate"></a>CUserToolsManager::SaveState  
 在 Windows 注册表中存储有关用户工具的信息。  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 向 Windows 注册表项的路径。  
  
### <a name="return-value"></a>返回值  
 如果成功，则保存状态的非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 该方法将存储的当前状态`CUserToolsManager`Windows 注册表中的对象。  
  
 通常情况下，不需要直接调用此方法[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)自动作为应用程序的工作区中序列化过程的一部分调用。  
  
##  <a name="setdefext"></a>CUserToolsManager::SetDefExt  
 指定默认扩展插件，**文件打开**对话框中 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**的选项卡上**自定义**对话框。  
  
```  
void SetDefExt(const CString& strDefExt);
```  
  
### <a name="parameters"></a>参数  
 [in] `strDefExt`  
 文本字符串，其中包含默认文件扩展名。  
  
### <a name="remarks"></a>备注  
 调用此方法以指定默认文件扩展名**文件打开**对话框中，当用户选择要与用户工具相关联的应用程序时显示。 默认值为"exe"。  
  
##  <a name="setfilter"></a>CUserToolsManager::SetFilter  
 指定该文件筛选**文件打开**对话框中 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**的选项卡上**自定义**对话框。  
  
```  
void SetFilter(const CString& strFilter);
```  
  
### <a name="parameters"></a>参数  
 [in] `strFilter`  
 指定的筛选器。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 类](../../mfc/reference/cwinappex-class.md)   
 [CUserTool 类](../../mfc/reference/cusertool-class.md)

