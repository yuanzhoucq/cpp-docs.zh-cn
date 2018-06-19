---
title: CUserToolsManager 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CUserToolsManager [MFC], CUserToolsManager
- CUserToolsManager [MFC], CreateNewTool
- CUserToolsManager [MFC], FindTool
- CUserToolsManager [MFC], GetArgumentsMenuID
- CUserToolsManager [MFC], GetDefExt
- CUserToolsManager [MFC], GetFilter
- CUserToolsManager [MFC], GetInitialDirMenuID
- CUserToolsManager [MFC], GetMaxTools
- CUserToolsManager [MFC], GetToolsEntryCmd
- CUserToolsManager [MFC], GetUserTools
- CUserToolsManager [MFC], InvokeTool
- CUserToolsManager [MFC], IsUserToolCmd
- CUserToolsManager [MFC], LoadState
- CUserToolsManager [MFC], MoveToolDown
- CUserToolsManager [MFC], MoveToolUp
- CUserToolsManager [MFC], RemoveTool
- CUserToolsManager [MFC], SaveState
- CUserToolsManager [MFC], SetDefExt
- CUserToolsManager [MFC], SetFilter
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eaa99952daf401132768d9be5d4c589b5fdbee52
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376192"
---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager 类
保持的集合[CUserTool 类](../../mfc/reference/cusertool-class.md)应用程序中的对象。 用户工具是运行外部应用程序的菜单项。 `CUserToolsManager` 对象使用户或开发人员能够将新的用户工具添加到应用程序中。 它支持与用户工具关联的命令的执行，并将与用户工具相关的信息保存到 Windows 注册表中。  
  
## <a name="syntax"></a>语法  
  
```  
class CUserToolsManager : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|构造一个 `CUserToolsManager`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CUserToolsManager::CreateNewTool](#createnewtool)|创建一个新的用户工具。|  
|[CUserToolsManager::FindTool](#findtool)|返回指向`CMFCUserTool`与指定的命令 ID 相关联的对象|  
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|返回与关联的资源 ID**参数**上的菜单**工具**选项卡**自定义**对话框。|  
|[CUserToolsManager::GetDefExt](#getdefext)|返回的默认扩展名**文件打开**对话框 ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) 中使用**命令**字段上**工具**选项卡**自定义**对话框。|  
|[CUserToolsManager::GetFilter](#getfilter)|返回文件筛选器**文件打开**对话框 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段上**工具**选项卡**自定义**对话框。|  
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|返回与关联的资源 ID**初始目录**上的菜单**工具**选项卡**自定义**对话框。|  
|[CUserToolsManager::GetMaxTools](#getmaxtools)|应用程序中返回的最大可分配的用户工具数。|  
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|返回用户工具的菜单项占位符的命令 ID。|  
|[CUserToolsManager::GetUserTools](#getusertools)|返回对用户工具列表中的引用。|  
|[CUserToolsManager::InvokeTool](#invoketool)|执行具有指定的命令 id。 该用户工具关联的应用程序|  
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|确定命令 ID 是否与用户工具相关联。|  
|[CUserToolsManager::LoadState](#loadstate)|从 Windows 注册表加载用户工具相关的信息。|  
|[CUserToolsManager::MoveToolDown](#movetooldown)|用户工具列表中向下移动指定的用户工具。|  
|[CUserToolsManager::MoveToolUp](#movetoolup)|在用户工具的列表中向上移动指定的用户工具。|  
|[CUserToolsManager::RemoveTool](#removetool)|从应用程序中移除指定的用户工具。|  
|[CUserToolsManager::SaveState](#savestate)|在 Windows 注册表中存储用户工具相关的信息。|  
|[CUserToolsManager::SetDefExt](#setdefext)|指定的默认扩展，**文件打开**对话框 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段上**工具**选项卡**自定义**对话框。|  
|[CUserToolsManager::SetFilter](#setfilter)|指定该文件筛选器**文件打开**对话框 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段上**工具**选项卡**自定义**对话框。|  
  
## <a name="remarks"></a>备注  
 若要将用户工具合并到你的应用程序，你必须：  
  
 1. 保留一个菜单项和工具的一个用户菜单项关联的命令 ID。  
  
 2. 保留每个用户工具，用户可以在你的应用程序中定义的顺序的命令 ID。  
  
 3. 调用[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)方法并提供以下参数： 菜单命令 ID、 第一个用户工具命令 ID 和最后一个用户工具命令 id。  
  
 应该仅一个全局`CUserToolsManager`每个应用程序的对象。  
  
 用户工具的示例，请参阅 VisualStudioDemo 示例项目。  
  
## <a name="example"></a>示例  
 下面的示例演示如何检索到的引用`CUserToolsManager`对象以及如何创建新的用户工具。 此代码片段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CUserToolsManager`  
  
## <a name="requirements"></a>要求  
 **标头：** afxusertoolsmanager.h  
  
##  <a name="createnewtool"></a>  CUserToolsManager::CreateNewTool  
 创建一个新的用户工具。  
  
```  
CUserTool* CreateNewTool();
```  
  
### <a name="return-value"></a>返回值  
 指向新创建的用户工具，或`NULL`如果用户工具数目超过了最大值。 返回的类型是传递到的类型相同`CWinAppEx::EnableUserTools`作为`pToolRTC`参数。  
  
### <a name="remarks"></a>备注  
 此方法的调用中提供的范围内找到第一个可用的菜单命令 ID [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)并将用户工具分配此 id。  
  
 如果的工具数已达到最大值，此方法失败。 在范围内的所有命令 Id 都分配给用户工具时，将发生这种情况。 你可以通过调用检索工具的最大数[CUserToolsManager::GetMaxTools](#getmaxtools)。 你可以通过调用获取到工具列表的访问权限[CUserToolsManager::GetUserTools](#getusertools)方法。  
  
##  <a name="cusertoolsmanager"></a>  CUserToolsManager::CUserToolsManager  
 构造一个 `CUserToolsManager`。 每个应用程序必须具有最多一个用户工具管理器。  
  
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
 框架作为占位符用于用户的工具菜单的命令 ID 的无符号的整数。  
  
 [in] `uiCmdFirst`  
 第一个用户工具命令的命令 ID。  
  
 [in] `uiCmdLast`  
 最后一个用户工具命令的命令 ID。  
  
 [in] `pToolRTC`  
 类的[CUserToolsManager::CreateNewTool](#createnewtool)创建。 通过使用此类，你可以使用的派生的类型[CUserTool 类](../../mfc/reference/cusertool-class.md)而不是默认实现。  
  
 [in] `uArgMenuID`  
 自变量弹出菜单的菜单资源 ID。  
  
 [in] `uInitDirMenuID`  
 初始目录弹出菜单的菜单资源 ID。  
  
### <a name="remarks"></a>备注  
 请勿调用此构造函数。 而应调用[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)启用用户工具，并调用[CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager)用于获取指向`CUserToolsManager`。 有关详细信息，请参阅[用户定义的工具](../../mfc/user-defined-tools.md)。  
  
##  <a name="findtool"></a>  CUserToolsManager::FindTool  
 返回指向[CUserTool 类](../../mfc/reference/cusertool-class.md)与指定的命令 ID 相关联的对象  
  
```  
CUserTool* FindTool(UINT uiCmdId) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdId`  
 菜单命令标识符。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CUserTool 类](../../mfc/reference/cusertool-class.md)或`CUserTool`-派生对象，如果成功; 否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 当`FindTool`是成功，则返回的类型为的类型相同`pToolRTC`参数[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。  
  
##  <a name="getargumentsmenuid"></a>  CUserToolsManager::GetArgumentsMenuID  
 返回与关联的资源 ID**参数**上的菜单**工具**选项卡**自定义**对话框。  
  
```  
UINT GetArgumentsMenuID() const;  
```  
  
### <a name="return-value"></a>返回值  
 菜单资源的标识符。  
  
### <a name="remarks"></a>备注  
 `uArgMenuID`参数[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)指定资源的 ID。  
  
##  <a name="getdefext"></a>  CUserToolsManager::GetDefExt  
 返回的默认扩展名**文件打开**对话框 ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) 中使用**命令**字段上**工具**选项卡**自定义**对话框。  
  
```  
const CString& GetDefExt() const;  
```  
  
### <a name="return-value"></a>返回值  
 对引用`CString`包含扩展的对象。  
  
##  <a name="getfilter"></a>  CUserToolsManager::GetFilter  
 返回文件筛选器**文件打开**对话框 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段上**工具**选项卡**自定义**对话框。  
  
```  
const CString& GetFilter() const;  
```  
  
### <a name="return-value"></a>返回值  
 对引用`CString`包含的筛选器的对象。  
  
##  <a name="getinitialdirmenuid"></a>  CUserToolsManager::GetInitialDirMenuID  
 返回与关联的资源 ID**初始目录**上的菜单**工具**选项卡**自定义**对话框。  
  
```  
UINT GetInitialDirMenuID() const;  
```  
  
### <a name="return-value"></a>返回值  
 菜单资源标识符。  
  
### <a name="remarks"></a>备注  
 中指定返回的 ID`uInitDirMenuID`参数[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。  
  
##  <a name="getmaxtools"></a>  CUserToolsManager::GetMaxTools  
 应用程序中返回的最大可分配的用户工具数。  
  
```  
int GetMaxTools() const;  
```  
  
### <a name="return-value"></a>返回值  
 可以分配的用户工具最大数量。  
  
### <a name="remarks"></a>备注  
 调用此方法可检索的最大可以分配应用程序中的工具数。 此数字是从范围中的 Id 数`uiCmdFirst`通过`uiCmdLast`参数传递给[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。  
  
##  <a name="gettoolsentrycmd"></a>  CUserToolsManager::GetToolsEntryCmd  
 返回用户工具的菜单项占位符的命令 ID。  
  
```  
UINT GetToolsEntryCmd() const;  
```  
  
### <a name="return-value"></a>返回值  
 占位符的命令 ID。  
  
### <a name="remarks"></a>备注  
 若要启用用户工具，请调用[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。 `uiCmdToolsDummy`参数指定工具条目命令的命令 ID。 此方法返回工具条目命令 id。 在菜单中使用该 ID，只要它时被替换用户工具列表中显示的菜单。  
  
##  <a name="getusertools"></a>  CUserToolsManager::GetUserTools  
 返回对用户工具列表中的引用。  
  
```  
const CObList& GetUserTools() const;  
```  
  
### <a name="return-value"></a>返回值  
 常量引用到[CObList 类](../../mfc/reference/coblist-class.md)对象，其中包含用户工具的列表。  
  
### <a name="remarks"></a>备注  
 调用此方法来检索其中的用户列表工具[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)对象维护。 由类型的对象表示每个用户工具[CUserTool 类](../../mfc/reference/cusertool-class.md)或从派生的类型`CUserTool`。 类型由指定`pToolRTC`参数在调用时[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)若要启用用户工具。  
  
##  <a name="invoketool"></a>  CUserToolsManager::InvokeTool  
 执行具有指定的命令 id。 该用户工具关联的应用程序  
  
```  
BOOL InvokeTool(UINT uiCmdId);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdId`  
 与用户工具关联的菜单命令 ID。  
  
### <a name="return-value"></a>返回值  
 如果成功，则执行与用户工具关联的命令则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此方法以执行与用户关联的应用程序工具具有由指定的命令 ID `uiCmdId`。  
  
##  <a name="isusertoolcmd"></a>  CUserToolsManager::IsUserToolCmd  
 确定命令 ID 是否与用户工具相关联。  
  
```  
BOOL IsUserToolCmd(UINT uiCmdId) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdId`  
 菜单项是命令 ID。  
  
### <a name="return-value"></a>返回值  
 非零，如果给定的命令 ID 与用户工具相关联否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法检查命令 ID 范围中是否为给定的命令 ID。 在调用时指定的范围[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)若要启用用户工具。  
  
##  <a name="loadstate"></a>  CUserToolsManager::LoadState  
 从 Windows 注册表加载用户工具相关的信息。  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 Windows 注册表项的路径。  
  
### <a name="return-value"></a>返回值  
 如果已成功，则加载状态，则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法加载的状态`CUserToolsManager`从 Windows 注册表的对象。  
  
 通常情况下，不调用此方法直接。 [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)调用其作为工作区中初始化过程的一部分。  
  
##  <a name="movetooldown"></a>  CUserToolsManager::MoveToolDown  
 用户工具列表中向下移动指定的用户工具。  
  
```  
BOOL MoveToolDown(CUserTool* pTool);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTool`  
 指定要移动的用户工具。  
  
### <a name="return-value"></a>返回值  
 如果成功，则向下移动用户工具则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 如果此方法失败该工具，`pTool`指定不在内部列表或如果该工具是在列表中最后一个。  
  
##  <a name="movetoolup"></a>  CUserToolsManager::MoveToolUp  
 在用户工具的列表中向上移动指定的用户工具。  
  
```  
BOOL MoveToolUp(CUserTool* pTool);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTool`  
 指定要移动的用户工具。  
  
### <a name="return-value"></a>返回值  
 如果成功，则向上移动用户工具则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 如果此方法失败该工具，`pTool`参数指定不在内部列表或如果该工具是在列表中的第一个工具项。  
  
##  <a name="removetool"></a>  CUserToolsManager::RemoveTool  
 从应用程序中移除指定的用户工具。  
  
```  
BOOL RemoveTool(CUserTool* pTool);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `pTool`  
 指向要删除的用户工具的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果该工具已成功删除。 否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 如果已成功删除该工具，此方法会删除`pTool`。  
  
##  <a name="savestate"></a>  CUserToolsManager::SaveState  
 在 Windows 注册表中存储用户工具相关的信息。  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 向 Windows 注册表项的路径。  
  
### <a name="return-value"></a>返回值  
 如果成功，则保存状态则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 该方法将存储的当前状态`CUserToolsManager`Windows 注册表中的对象。  
  
 通常情况下，不需要直接调用此方法[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)自动作为应用程序的工作区中序列化过程的一部分调用。  
  
##  <a name="setdefext"></a>  CUserToolsManager::SetDefExt  
 指定的默认扩展，**文件打开**对话框 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段上**工具**选项卡**自定义**对话框。  
  
```  
void SetDefExt(const CString& strDefExt);
```  
  
### <a name="parameters"></a>参数  
 [in] `strDefExt`  
 包含默认文件扩展名的文本字符串。  
  
### <a name="remarks"></a>备注  
 调用此方法以指定在默认文件扩展名**文件打开**对话框中，当用户选择要与用户工具相关联的应用程序时显示。 默认值为"exe"。  
  
##  <a name="setfilter"></a>  CUserToolsManager::SetFilter  
 指定该文件筛选器**文件打开**对话框 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段上**工具**选项卡**自定义**对话框。  
  
```  
void SetFilter(const CString& strFilter);
```  
  
### <a name="parameters"></a>参数  
 [in] `strFilter`  
 指定的筛选器。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 类](../../mfc/reference/cwinappex-class.md)   
 [CUserTool 类](../../mfc/reference/cusertool-class.md)
