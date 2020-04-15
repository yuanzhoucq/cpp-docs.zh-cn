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
ms.openlocfilehash: c1f14657350c08679868299ce4878cca2ae10eec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373225"
---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager 类

维护应用程序中[CUserTool 类](../../mfc/reference/cusertool-class.md)对象的集合。 用户工具是运行外部应用程序的菜单项。 `CUserToolsManager` 对象使用户或开发人员能够将新的用户工具添加到应用程序中。 它支持与用户工具关联的命令的执行，并将与用户工具相关的信息保存到 Windows 注册表中。

## <a name="syntax"></a>语法

```
class CUserToolsManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[用户工具管理器：：用户工具管理器](#cusertoolsmanager)|构造一个 `CUserToolsManager`。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[用户工具管理器：：创建新工具](#createnewtool)|创建新的用户工具。|
|[用户工具管理器：：查找工具](#findtool)|返回指向与指定命令`CMFCUserTool`ID 关联的对象的指针。|
|[配置工具管理器：：获取参数菜单ID](#getargumentsmenuid)|返回与 **"自定义"** 对话框"**工具**"选项卡上的 **"参数"** 菜单关联的资源 ID。|
|[用户工具管理器：：获取DefExt](#getdefext)|返回 **"文件打开**"对话框 （ [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)） 在 **"自定义**"对话框"**工具**"选项卡上的 **"命令**"字段中使用的默认扩展名。|
|[用户工具管理器：：获取过滤器](#getfilter)|返回**文件打开**对话框 （ [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)） 在 **"自定义**"对话框"**工具"** 选项卡上的 **"命令**"字段中使用的文件筛选器。|
|[配置工具管理器：：获取初始DirMenuID](#getinitialdirmenuid)|返回与 **"自定义"** 对话框"**工具**"选项卡上 **"初始目录"** 菜单关联的资源 ID。|
|[用户工具管理器：：获取MaxTools](#getmaxtools)|返回可在应用程序中分配的最大用户工具数。|
|[用户工具管理器：：获取工具入口 Cmd](#gettoolsentrycmd)|返回用户工具的菜单项占位符的命令 ID。|
|[用户工具管理器：获取用户工具](#getusertools)|返回对用户工具列表的引用。|
|[用户工具管理器：：调用工具](#invoketool)|执行与具有指定命令 ID 的用户工具关联的应用程序。|
|[用户工具管理器：：用户工具Cmd](#isusertoolcmd)|确定命令 ID 是否与用户工具关联。|
|[用户工具管理器：：加载状态](#loadstate)|从 Windows 注册表加载有关用户工具的信息。|
|[用户工具管理器：移动工具向下](#movetooldown)|在用户工具列表中向下移动指定的用户工具。|
|[用户工具管理器：移动工具](#movetoolup)|在用户工具列表中向上移动指定的用户工具。|
|[用户工具管理器：：删除工具](#removetool)|从应用程序中删除指定的用户工具。|
|[CUserTools 管理器：：保存状态](#savestate)|在 Windows 注册表中存储有关用户工具的信息。|
|[用户工具管理器：：SetDefExt](#setdefext)|指定 **"文件打开**"对话框[（CFileDialog 类](../../mfc/reference/cfiledialog-class.md)） 在 **"自定义**"对话框"**工具**"选项卡上的 **"命令**"字段中使用的默认扩展名。|
|[用户工具管理器：：设置筛选器](#setfilter)|指定**文件**打开对话框 （ [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)） 在 **"自定义**"对话框"**工具"** 选项卡上的 **"命令**"字段中使用的文件筛选器。|

## <a name="remarks"></a>备注

要将用户工具合并到应用程序中，您必须：

1. 为用户工具菜单条目保留菜单项和关联的命令 ID。

2. 为用户可以在应用程序中定义的每个用户工具保留顺序命令 ID。

3. 调用[CWinAppEx：启用UserTools](../../mfc/reference/cwinappex-class.md#enableusertools)方法并提供以下参数：菜单命令 ID、第一个用户工具命令 ID 和最后一个用户工具命令 ID。

每个应用程序应只有一个`CUserToolsManager`全局对象。

有关用户工具的示例，请参阅 VisualStudioDemo 示例项目。

## <a name="example"></a>示例

下面的示例演示如何检索对`CUserToolsManager`对象的引用以及如何创建新的用户工具。 此代码段是[可视化工作室演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>要求

**标题：** afxuser工具管理器.h

## <a name="cusertoolsmanagercreatenewtool"></a><a name="createnewtool"></a>用户工具管理器：：创建新工具

创建新的用户工具。

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>返回值

指向新创建的用户工具的指针，如果用户工具数超过最大值，则指向 NULL。 返回的类型与传递给`CWinAppEx::EnableUserTools` *pToolRTC*参数的类型相同。

### <a name="remarks"></a>备注

此方法查找[CWinAppEx：：启用UserTools](../../mfc/reference/cwinappex-class.md#enableusertools)并在调用中提供的范围中提供的第一个可用菜单命令 ID，并分配此 ID 的用户工具。

如果工具数已达到最大值，则该方法将失败。 当将范围内的所有命令指示指定给用户工具时，将发生这种情况。 您可以通过调用[CUserToolsManager 检索工具的最大数量：：GetMaxTools](#getmaxtools)。 您可以通过调用[CUserToolsManager：：：getUserTools](#getusertools)方法访问工具列表。

## <a name="cusertoolsmanagercusertoolsmanager"></a><a name="cusertoolsmanager"></a>用户工具管理器：：用户工具管理器

构造一个 `CUserToolsManager`。 每个应用程序必须最多有一个用户工具管理器。

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
[在]框架用作用户工具菜单的命令 ID 的占位符的无符号整数。

*uiCmdFirst*<br/>
[在]第一个用户工具命令的命令 ID。

*uiCmdLast*<br/>
[在]最后一个用户工具命令的命令 ID。

*pToolRTC*<br/>
[在][CUserToolsManager：创建新工具](#createnewtool)创建的类。 通过使用此类，可以使用派生类型的[CUserTool 类](../../mfc/reference/cusertool-class.md)而不是默认实现。

*uArgMenuID*<br/>
[在]参数弹出菜单的菜单资源 ID。

*乌伊尼特迪尔梅尼*<br/>
[在]初始目录弹出菜单的菜单资源 ID。

### <a name="remarks"></a>备注

不要调用此构造函数。 相反，调用[CWinAppEx：：启用用户工具](../../mfc/reference/cwinappex-class.md#enableusertools)以启用用户工具，并调用[CWinAppEx：：getUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager)以获取指向`CUserToolsManager`的指针。 有关详细信息，请参阅[用户定义的工具](../../mfc/user-defined-tools.md)。

## <a name="cusertoolsmanagerfindtool"></a><a name="findtool"></a>用户工具管理器：：查找工具

返回指向与指定命令 ID 关联的[CUserTool 类](../../mfc/reference/cusertool-class.md)对象的指针。

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>参数

*乌伊CmDId*<br/>
[在]菜单命令标识符。

### <a name="return-value"></a>返回值

指向[CUserTool 类](../../mfc/reference/cusertool-class.md)或`CUserTool`派生对象的指针（如果成功）;否则 NULL。

### <a name="remarks"></a>备注

成功`FindTool`后，返回的类型与 CWinAppEx*的 pToolRTC*参数类型相同[：：启用用户工具](../../mfc/reference/cwinappex-class.md#enableusertools)。

## <a name="cusertoolsmanagergetargumentsmenuid"></a><a name="getargumentsmenuid"></a>配置工具管理器：：获取参数菜单ID

返回与 **"自定义"** 对话框"**工具**"选项卡上的 **"参数"** 菜单关联的资源 ID。

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>返回值

菜单资源的标识符。

### <a name="remarks"></a>备注

[CWinAppEx 的](../../mfc/reference/cwinappex-class.md#enableusertools) *uArgMenuID*参数：启用用户工具指定资源的 ID。

## <a name="cusertoolsmanagergetdefext"></a><a name="getdefext"></a>用户工具管理器：：获取DefExt

返回 **"文件打开**"对话框 （ [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)） 在 **"自定义**"对话框"**工具**"选项卡上的 **"命令**"字段中使用的默认扩展名。

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>返回值

对包含扩展`CString`的对象的引用。

## <a name="cusertoolsmanagergetfilter"></a><a name="getfilter"></a>用户工具管理器：：获取过滤器

返回**文件打开**对话框 （ [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)） 在 **"自定义**"对话框"**工具"** 选项卡上的 **"命令**"字段中使用的文件筛选器。

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>返回值

对包含筛选器`CString`的对象的引用。

## <a name="cusertoolsmanagergetinitialdirmenuid"></a><a name="getinitialdirmenuid"></a>配置工具管理器：：获取初始DirMenuID

返回与 **"自定义"** 对话框"**工具**"选项卡上 **"初始目录"** 菜单关联的资源 ID。

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>返回值

菜单资源标识符。

### <a name="remarks"></a>备注

返回的 ID 在 CWinAppEx 的*uInitDirMenuID*参数中指定[：启用用户工具](../../mfc/reference/cwinappex-class.md#enableusertools)。

## <a name="cusertoolsmanagergetmaxtools"></a><a name="getmaxtools"></a>用户工具管理器：：获取MaxTools

返回可在应用程序中分配的最大用户工具数。

```
int GetMaxTools() const;
```

### <a name="return-value"></a>返回值

可分配的最大用户工具数。

### <a name="remarks"></a>备注

调用此方法以检索可在应用程序中分配的最大工具数。 此数字是从*uiCmdFirst*到您传递给[CWinAppEx](../../mfc/reference/cwinappex-class.md#enableusertools)的*uiCmdLast*参数范围内的 ID 数：启用用户工具 。

## <a name="cusertoolsmanagergettoolsentrycmd"></a><a name="gettoolsentrycmd"></a>用户工具管理器：：获取工具入口 Cmd

返回用户工具的菜单项占位符的命令 ID。

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>返回值

占位符的命令 ID。

### <a name="remarks"></a>备注

要启用用户工具，请致电[CWinAppEx：：启用用户工具](../../mfc/reference/cwinappex-class.md#enableusertools)。 *uiCmdToolsDummy*参数指定工具输入命令的命令 ID。 此方法返回工具条目命令 ID。 无论该 ID 在菜单中使用何处，当菜单出现时，该 ID 将被用户工具列表替换。

## <a name="cusertoolsmanagergetusertools"></a><a name="getusertools"></a>用户工具管理器：获取用户工具

返回对用户工具列表的引用。

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>返回值

对包含用户工具列表的[CObList 类](../../mfc/reference/coblist-class.md)对象的引用。

### <a name="remarks"></a>备注

调用此方法以检索[CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)对象维护的用户工具列表。 每个用户工具由[CUserTool 类](../../mfc/reference/cusertool-class.md)类型的对象或派生自`CUserTool`的类型表示。 当您调用[CWinAppEx：：启用用户工具启用用户工具](../../mfc/reference/cwinappex-class.md#enableusertools)时，该类型由*pToolRTC*参数指定。

## <a name="cusertoolsmanagerinvoketool"></a><a name="invoketool"></a>用户工具管理器：：调用工具

执行与具有指定命令 ID 的用户工具关联的应用程序。

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>参数

*乌伊CmDId*<br/>
[在]与用户工具关联的菜单命令 ID。

### <a name="return-value"></a>返回值

如果成功执行与用户工具关联的命令，则非零;否则 0。

### <a name="remarks"></a>备注

调用此方法以执行与具有*uiCmdId*指定的命令 ID 的用户工具关联的应用程序。

## <a name="cusertoolsmanagerisusertoolcmd"></a><a name="isusertoolcmd"></a>用户工具管理器：：用户工具Cmd

确定命令 ID 是否与用户工具关联。

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>参数

*乌伊CmDId*<br/>
[在]菜单项的命令 ID。

### <a name="return-value"></a>返回值

如果给定的命令 ID 与用户工具关联，则非零;否则 0。

### <a name="remarks"></a>备注

此方法检查给定的命令 ID 是否位于命令 ID 范围内。 当您调用[CWinAppEx 时，您可以指定范围：启用用户工具](../../mfc/reference/cwinappex-class.md#enableusertools)以启用用户工具。

## <a name="cusertoolsmanagerloadstate"></a><a name="loadstate"></a>用户工具管理器：：加载状态

从 Windows 注册表加载有关用户工具的信息。

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]Windows 注册表项的路径。

### <a name="return-value"></a>返回值

如果状态已成功加载，则非零;否则 0。

### <a name="remarks"></a>备注

此方法从 Windows 注册表加载`CUserToolsManager`对象的状态。

通常，您不会直接调用此方法。 [CWinAppEx：LoadState](../../mfc/reference/cwinappex-class.md#loadstate)将其称为工作区初始化过程的一部分。

## <a name="cusertoolsmanagermovetooldown"></a><a name="movetooldown"></a>用户工具管理器：移动工具向下

在用户工具列表中向下移动指定的用户工具。

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>参数

*pTool*<br/>
[在]指定要移动的用户工具。

### <a name="return-value"></a>返回值

如果用户工具已成功向下移动，则非零;否则 0。

### <a name="remarks"></a>备注

如果*pTool*指定的工具不在内部列表中，或者该工具在列表中是最后一个，则该方法将失败。

## <a name="cusertoolsmanagermovetoolup"></a><a name="movetoolup"></a>用户工具管理器：移动工具

在用户工具列表中向上移动指定的用户工具。

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>参数

*pTool*<br/>
[在]指定要移动的用户工具。

### <a name="return-value"></a>返回值

如果用户工具成功向上移动，则非零;否则 0。

### <a name="remarks"></a>备注

如果*pTool*参数指定的工具不在内部列表中，或者该工具是列表中的第一个工具项，则该方法将失败。

## <a name="cusertoolsmanagerremovetool"></a><a name="removetool"></a>用户工具管理器：：删除工具

从应用程序中删除指定的用户工具。

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>参数

*pTool*<br/>
[进出]指向要删除的用户工具的指针。

### <a name="return-value"></a>返回值

如果工具已成功删除，则为 TRUE。 否则为 FALSE。

### <a name="remarks"></a>备注

如果该工具已成功删除，则此方法将删除*pTool*。

## <a name="cusertoolsmanagersavestate"></a><a name="savestate"></a>CUserTools 管理器：：保存状态

在 Windows 注册表中存储有关用户工具的信息。

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]Windows 注册表项的路径。

### <a name="return-value"></a>返回值

如果成功保存状态，则非零;否则 0。

### <a name="remarks"></a>备注

该方法在 Windows 注册表中存储`CUserToolsManager`对象的当前状态。

通常，您不需要直接调用此方法[CWinAppEx：：SaveState](../../mfc/reference/cwinappex-class.md#savestate)自动调用它作为应用程序的工作区序列化过程的一部分。

## <a name="cusertoolsmanagersetdefext"></a><a name="setdefext"></a>用户工具管理器：：SetDefExt

指定 **"文件打开**"对话框[（CFileDialog 类](../../mfc/reference/cfiledialog-class.md)） 在 **"自定义**"对话框"**工具**"选项卡上的 **"命令**"字段中使用的默认扩展名。

```
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>参数

*斯特德夫克斯*<br/>
[在]包含默认文件名扩展名的文本字符串。

### <a name="remarks"></a>备注

调用此方法以在 **"文件打开"** 对话框中指定默认文件名扩展名，当用户选择要与用户工具关联的应用程序时将显示该对话框。 默认值为"exe"。

## <a name="cusertoolsmanagersetfilter"></a><a name="setfilter"></a>用户工具管理器：：设置筛选器

指定**文件**打开对话框 （ [CFileDialog 类](../../mfc/reference/cfiledialog-class.md)） 在 **"自定义**"对话框"**工具"** 选项卡上的 **"命令**"字段中使用的文件筛选器。

```
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>参数

*斯特过滤器*<br/>
[在]指定筛选器。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)<br/>
[用户工具类](../../mfc/reference/cusertool-class.md)
