---
title: CUserToolsManager 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 405260d4bc2f7cdf163dbd7a00f342b8afc87d48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668102"
---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager 类

维护的集合[CUserTool 类](../../mfc/reference/cusertool-class.md)应用程序中的对象。 用户工具是运行外部应用程序的菜单项。 `CUserToolsManager` 对象使用户或开发人员能够将新的用户工具添加到应用程序中。 它支持与用户工具关联的命令的执行，并将与用户工具相关的信息保存到 Windows 注册表中。

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
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|返回与之关联的资源 ID**自变量**菜单上的**工具**选项卡**自定义**对话框。|
|[CUserToolsManager::GetDefExt](#getdefext)|返回默认扩展插件**文件打开**对话框的 ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) 中使用**命令**字段**工具**选项卡**自定义**对话框。|
|[CUserToolsManager::GetFilter](#getfilter)|返回的文件筛选器**文件打开**对话框的 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**选项卡**自定义**对话框。|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|返回与之关联的资源 ID**初始目录**菜单上的**工具**选项卡**自定义**对话框。|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|在应用程序中返回可以分配的用户工具的最大数目。|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|返回用户工具的菜单项占位符的命令 ID。|
|[CUserToolsManager::GetUserTools](#getusertools)|返回到用户工具列表的引用。|
|[CUserToolsManager::InvokeTool](#invoketool)|执行与具有指定的命令 id。 该用户工具相关联的应用程序|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|确定是否与用户工具相关联的命令 ID。|
|[CUserToolsManager::LoadState](#loadstate)|从 Windows 注册表加载用户工具相关的信息。|
|[CUserToolsManager::MoveToolDown](#movetooldown)|用户工具列表中向下移动指定的用户工具。|
|[CUserToolsManager::MoveToolUp](#movetoolup)|在用户工具列表中向上移动指定的用户工具。|
|[CUserToolsManager::RemoveTool](#removetool)|从应用程序中删除指定的用户工具。|
|[CUserToolsManager::SaveState](#savestate)|在 Windows 注册表中存储有关用户工具的信息。|
|[CUserToolsManager::SetDefExt](#setdefext)|指定默认扩展插件的**文件打开**对话框的 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**选项卡**自定义**对话框。|
|[CUserToolsManager::SetFilter](#setfilter)|指定文件的筛选器**文件打开**对话框的 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**选项卡**自定义**对话框。|

## <a name="remarks"></a>备注

若要将用户工具合并到你的应用程序，必须：

1. 保留的菜单项和用户工具菜单项关联的命令 ID。

2. 保留每个用户工具，用户可以在你的应用程序中定义的顺序的命令 ID。

3. 调用[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)方法并提供以下参数： 菜单命令 ID、 第一个用户工具命令 ID 和最后一个用户工具的命令 id。

应该只有一个全局`CUserToolsManager`每个应用程序的对象。

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

一个指向新创建的用户工具或如果用户工具数已超过最大值为 NULL。 返回的类型是传递到的类型相同`CWinAppEx::EnableUserTools`作为*pToolRTC*参数。

### <a name="remarks"></a>备注

此方法调用中提供的范围内找到第一个可用的菜单命令 ID [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) ，并将用户工具分配此 id。

如果工具数已达到最大值，此方法失败。 当范围内的所有命令 Id 将都分配给用户工具时，将发生这种情况。 可以通过调用检索工具的最大数目[CUserToolsManager::GetMaxTools](#getmaxtools)。 可以通过调用获取到工具列表访问权限[CUserToolsManager::GetUserTools](#getusertools)方法。

##  <a name="cusertoolsmanager"></a>  CUserToolsManager::CUserToolsManager

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

*uiCmdToolsDummy*<br/>
[in]无符号的整数，该框架作为占位符用于用户工具菜单的命令 ID。

*uiCmdFirst*<br/>
[in]第一个用户工具命令的命令 ID。

*uiCmdLast*<br/>
[in]最后一个用户工具命令的命令 ID。

*pToolRTC*<br/>
[in]类的[CUserToolsManager::CreateNewTool](#createnewtool)创建。 通过使用此类，您可以使用的派生的类型[CUserTool 类](../../mfc/reference/cusertool-class.md)而不是默认实现。

*uArgMenuID*<br/>
[in]参数弹出菜单的菜单资源 ID。

*uInitDirMenuID*<br/>
[in]初始目录弹出菜单的菜单资源 ID。

### <a name="remarks"></a>备注

请勿调用此构造函数。 改为调用[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)启用的用户工具，并调用[CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager)若要获取的指针`CUserToolsManager`。 有关详细信息，请参阅[用户定义的工具](../../mfc/user-defined-tools.md)。

##  <a name="findtool"></a>  CUserToolsManager::FindTool

返回指向[CUserTool 类](../../mfc/reference/cusertool-class.md)与指定的命令 ID 相关联的对象

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>参数

*uiCmdId*<br/>
[in]菜单命令标识符。

### <a name="return-value"></a>返回值

一个指向[CUserTool 类](../../mfc/reference/cusertool-class.md)或`CUserTool`-如果派生的对象成功; 否则为 NULL。

### <a name="remarks"></a>备注

当`FindTool`是成功，则返回的类型为的类型相同*pToolRTC*参数[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。

##  <a name="getargumentsmenuid"></a>  CUserToolsManager::GetArgumentsMenuID

返回与之关联的资源 ID**自变量**菜单上的**工具**选项卡**自定义**对话框。

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>返回值

菜单资源的标识符。

### <a name="remarks"></a>备注

*UArgMenuID*的参数[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)指定的资源 ID。

##  <a name="getdefext"></a>  CUserToolsManager::GetDefExt

返回默认扩展插件**文件打开**对话框的 ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) 中使用**命令**字段**工具**选项卡**自定义**对话框。

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>返回值

对引用`CString`包含扩展的对象。

##  <a name="getfilter"></a>  CUserToolsManager::GetFilter

返回的文件筛选器**文件打开**对话框的 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**选项卡**自定义**对话框。

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>返回值

对引用`CString`对象，其中包含筛选器。

##  <a name="getinitialdirmenuid"></a>  CUserToolsManager::GetInitialDirMenuID

返回与之关联的资源 ID**初始目录**菜单上的**工具**选项卡**自定义**对话框。

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>返回值

菜单资源标识符。

### <a name="remarks"></a>备注

中指定返回的 ID *uInitDirMenuID*的参数[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。

##  <a name="getmaxtools"></a>  CUserToolsManager::GetMaxTools

在应用程序中返回可以分配的用户工具的最大数目。

```
int GetMaxTools() const;
```

### <a name="return-value"></a>返回值

用户工具可分配最大数目。

### <a name="remarks"></a>备注

调用此方法以检索工具，可以在应用程序中分配的最大数目。 此数字是从范围中的 Id 号*uiCmdFirst*通过*uiCmdLast*参数传递给[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。

##  <a name="gettoolsentrycmd"></a>  CUserToolsManager::GetToolsEntryCmd

返回用户工具的菜单项占位符的命令 ID。

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>返回值

占位符的命令 ID。

### <a name="remarks"></a>备注

若要启用用户工具，请调用[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)。 *UiCmdToolsDummy*参数指定工具条目命令的命令 ID。 此方法返回工具项的命令 id。 在菜单中将使用该 ID，无论它时被替换的用户工具列表会显示的菜单。

##  <a name="getusertools"></a>  CUserToolsManager::GetUserTools

返回到用户工具列表的引用。

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>返回值

常量引用[CObList 类](../../mfc/reference/coblist-class.md)对象，其中包含的用户工具列表。

### <a name="remarks"></a>备注

调用此方法以检索用户的列表工具[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)对象维护。 每个用户工具由类型的对象表示[CUserTool 类](../../mfc/reference/cusertool-class.md)派生的类型或`CUserTool`。 指定的类型*pToolRTC*参数调用时[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)若要启用用户工具。

##  <a name="invoketool"></a>  CUserToolsManager::InvokeTool

执行与具有指定的命令 id。 该用户工具相关联的应用程序

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>参数

*uiCmdId*<br/>
[in]与用户工具关联的菜单命令 ID。

### <a name="return-value"></a>返回值

如果与用户工具关联的命令执行成功，则非零值否则为 0。

### <a name="remarks"></a>备注

调用此方法以执行与用户关联的应用程序工具，它具有由指定的命令 ID *uiCmdId*。

##  <a name="isusertoolcmd"></a>  CUserToolsManager::IsUserToolCmd

确定是否与用户工具相关联的命令 ID。

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>参数

*uiCmdId*<br/>
[in]菜单项的命令 ID。

### <a name="return-value"></a>返回值

如果给定的命令 ID 的用户工具; 与相关联，非零值否则为 0。

### <a name="remarks"></a>备注

此方法检查中的命令 ID 范围是否为给定的命令 ID。 在调用时指定的范围[CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools)若要启用用户工具。

##  <a name="loadstate"></a>  CUserToolsManager::LoadState

从 Windows 注册表加载用户工具相关的信息。

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
[in]Windows 注册表项的路径。

### <a name="return-value"></a>返回值

如果状态加载成功，则非零值否则为 0。

### <a name="remarks"></a>备注

此方法加载的状态`CUserToolsManager`Windows 注册表中的对象。

通常情况下，你不执行操作直接调用此方法。 [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)会调用该工作区初始化过程的一部分。

##  <a name="movetooldown"></a>  CUserToolsManager::MoveToolDown

用户工具列表中向下移动指定的用户工具。

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>参数

*pTool*<br/>
[in]指定要移动的用户工具。

### <a name="return-value"></a>返回值

如果成功，则向下移动用户工具，非零值否则为 0。

### <a name="remarks"></a>备注

如果此方法失败该工具的*pTool*指定不在内部列表或如果该工具是在列表中的最后。

##  <a name="movetoolup"></a>  CUserToolsManager::MoveToolUp

在用户工具列表中向上移动指定的用户工具。

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>参数

*pTool*<br/>
[in]指定要移动的用户工具。

### <a name="return-value"></a>返回值

如果成功，则向上移动用户工具，非零值否则为 0。

### <a name="remarks"></a>备注

如果此方法失败该工具的*pTool*参数指定的内部列表中不是或者如果该工具是第一个工具中的项列表。

##  <a name="removetool"></a>  CUserToolsManager::RemoveTool

从应用程序中删除指定的用户工具。

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>参数

*pTool*<br/>
[in、 out]一个指向要删除的用户工具。

### <a name="return-value"></a>返回值

如果成功移除了该工具，则为 TRUE。 否则为 FALSE。

### <a name="remarks"></a>备注

如果成功移除了该工具，则此方法删除*pTool*。

##  <a name="savestate"></a>  CUserToolsManager::SaveState

在 Windows 注册表中存储有关用户工具的信息。

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
[in]对 Windows 注册表项路径。

### <a name="return-value"></a>返回值

如果成功，则保存状态的非零值否则为 0。

### <a name="remarks"></a>备注

该方法将存储的当前状态`CUserToolsManager`Windows 注册表中的对象。

通常情况下，不需要直接调用此方法[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)自动作为应用程序的工作区序列化过程的一部分调用。

##  <a name="setdefext"></a>  CUserToolsManager::SetDefExt

指定默认扩展插件的**文件打开**对话框的 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**选项卡**自定义**对话框。

```
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>参数

*strDefExt*<br/>
[in]包含默认文件扩展名的文本字符串。

### <a name="remarks"></a>备注

调用此方法以指定在默认文件扩展名**文件打开**对话框中，当用户选择要与用户工具相关联的应用程序时显示。 默认值为"exe"。

##  <a name="setfilter"></a>  CUserToolsManager::SetFilter

指定文件的筛选器**文件打开**对话框的 ( [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)) 中使用**命令**字段**工具**选项卡**自定义**对话框。

```
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>参数

*strFilter*<br/>
[in]指定的筛选器。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)<br/>
[CUserTool 类](../../mfc/reference/cusertool-class.md)
