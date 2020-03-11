---
title: CContextMenuManager 类
ms.date: 11/04/2016
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
helpviewer_keywords:
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
ms.openlocfilehash: c8a51a33c69b09d0ecd61520b5f1c9ff18c290a0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78868985"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager 类

`CContextMenuManager` 对象管理快捷菜单（也称为上下文菜单）。

## <a name="syntax"></a>语法

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|构造 `CContextMenuManager` 对象。|
|`CContextMenuManager::~CContextMenuManager`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CContextMenuManager：： AddMenu](#addmenu)|添加新的快捷菜单。|
|[CContextMenuManager::GetMenuById](#getmenubyid)|返回与所提供资源 ID 相关联的菜单的句柄。|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|返回与所提供菜单名称匹配的菜单的句柄。|
|[CContextMenuManager::GetMenuNames](#getmenunames)|返回菜单名称的列表。|
|[CContextMenuManager：： LoadState](#loadstate)|加载存储在 Windows 注册表中的快捷菜单。|
|[CContextMenuManager：： ResetState](#resetstate)|从上下文菜单管理器中清除快捷菜单。|
|[CContextMenuManager：： SaveState](#savestate)|将快捷菜单保存到 Windows 注册表中。|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|控制在显示新的快捷菜单时，`CContextMenuManager` 是否关闭活动快捷菜单。|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|显示指定的快捷菜单。|
|[CContextMenuManager：： TrackPopupMenu](#trackpopupmenu)|显示指定的快捷菜单。 返回选定菜单命令的索引。|

## <a name="remarks"></a>备注

`CContextMenuManager` 管理快捷菜单，并确保它们具有一致的外观。

不应手动创建 `CContextMenuManager` 对象。 应用程序的框架会创建 `CContextMenuManager` 对象。 但是，在初始化应用程序时，应调用[CWinAppEx：： InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) 。 初始化上下文管理器后，使用方法[CWinAppEx：： GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)获取应用程序的上下文管理器的指针。

可以通过调用 `AddMenu`在运行时创建快捷菜单。 如果希望在不事先接收用户输入的情况下显示菜单，请调用 `ShowPopupMenu`。 若要创建菜单并等待用户输入，请使用 `TrackPopupMenu`。 `TrackPopupMenu` 返回所选命令的索引; 如果用户退出但不选择任何内容，则返回0。

`CContextMenuManager` 还可以将其状态保存并加载到 Windows 注册表中。

## <a name="example"></a>示例

下面的示例演示如何向 `CContextMenuManager` 对象添加菜单，以及在 `CContextMenuManager` 对象显示新的弹出菜单时如何关闭活动的弹出菜单。 此代码片段是[自定义页面示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>要求

**标头：** afxcontextmenumanager

##  <a name="addmenu"></a>CContextMenuManager：： AddMenu

向[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)添加新的快捷菜单。

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>parameters

*uiMenuNameResId*<br/>
中包含新菜单的名称的字符串的资源 ID。

*uiMenuResId*<br/>
中菜单资源 ID。

*lpszName*<br/>
中一个字符串，其中包含新菜单的名称。

### <a name="return-value"></a>返回值

如果方法成功，则为非零值;如果方法失败，则为0。

### <a name="remarks"></a>备注

如果*uiMenuResId*无效或 `CContextMenuManager`中已经存在具有相同名称的另一个菜单，则此方法将失败。

##  <a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager

构造[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)对象。

```
CContextMenuManager();
```

### <a name="remarks"></a>备注

在大多数情况下，不应手动创建 `CContextMenuManager`。 应用程序的框架会创建 `CContextMenuManager` 对象。 你应在应用程序的初始化过程中调用[CWinAppEx：： InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) 。 若要获取指向上下文管理器的指针，请调用[CWinAppEx：： GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)。

##  <a name="getmenubyid"></a>CContextMenuManager::GetMenuById

返回与给定资源 ID 相关联的菜单的句柄。

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>parameters

*nMenuResId*<br/>
中菜单的资源 ID。

### <a name="return-value"></a>返回值

如果找不到该菜单，则为关联的菜单的句柄或 `NULL`。

##  <a name="getmenubyname"></a>CContextMenuManager::GetMenuByName

返回特定菜单的句柄。

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>parameters

*lpszName*<br/>
中一个字符串，其中包含要检索的菜单的名称。

*puiOrigResID*<br/>
弄指向 UINT 的指针。 如果找到，此参数包含指定菜单的资源 ID。

### <a name="return-value"></a>返回值

与*lpszName*指定的名称相匹配的菜单的句柄。 如果没有名为*lpszName*的菜单，则为 NULL。

### <a name="remarks"></a>备注

如果此方法找到与*lpszName*匹配的菜单，则 `GetMenuByName` 将菜单资源 ID 存储在参数*puiOrigResID*中。

##  <a name="getmenunames"></a>CContextMenuManager::GetMenuNames

返回添加到[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)的菜单名称的列表。

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>parameters

*listOfNames*<br/>
弄对[CStringList](../../mfc/reference/cstringlist-class.md)参数的引用。 此方法将菜单名称的列表写入此参数。

##  <a name="loadstate"></a>CContextMenuManager：： LoadState

从 Windows 注册表加载与[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)关联的信息。

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>parameters

*lpszProfileName*<br/>
中包含注册表项的相对路径的字符串。

### <a name="return-value"></a>返回值

如果方法成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

*LpszProfileName*参数不是注册表项的绝对路径。 它是添加到应用程序的默认注册表项末尾的相对路径。 若要获取或设置默认的注册表项，请分别使用方法[CWinAppEx：： GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx：： SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) 。

使用方法[CContextMenuManager：： SaveState](#savestate)将快捷菜单保存到注册表中。

##  <a name="resetstate"></a>CContextMenuManager：： ResetState

清除与[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)关联的快捷菜单中的所有项。

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;如果发生失败，则为 FALSE。

### <a name="remarks"></a>备注

此方法会清除弹出菜单并将其从 `CContextMenuManager`中移除。

##  <a name="savestate"></a>CContextMenuManager：： SaveState

将与[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)关联的信息保存到 Windows 注册表中。

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>parameters

*lpszProfileName*<br/>
中包含注册表项的相对路径的字符串。

### <a name="return-value"></a>返回值

如果方法成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

*LpszProfileName*参数不是注册表项的绝对路径。 它是添加到应用程序的默认注册表项末尾的相对路径。 若要获取或设置默认的注册表项，请分别使用方法[CWinAppEx：： GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx：： SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) 。

使用方法[CContextMenuManager：： LoadState](#loadstate)从注册表加载快捷菜单。

##  <a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu

控制[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)在显示新的弹出菜单时是否关闭活动的弹出菜单。

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>parameters

*bSet*<br/>
中一个布尔参数，用于控制是否关闭活动的弹出菜单。 如果值为 TRUE，则指示活动弹出菜单未关闭。 FALSE 指示活动弹出菜单已关闭。

### <a name="remarks"></a>备注

默认情况下，`CContextMenuManager` 关闭活动的弹出菜单。

##  <a name="showpopupmenu"></a>CContextMenuManager::ShowPopupMenu

显示指定的快捷菜单。

```
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bRightAlign = FALSE);

virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bAutoDestroy = TRUE,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>parameters

*uiMenuResId*<br/>
中此方法将显示的菜单的资源 ID。

*x*<br/>
中工作区坐标中快捷菜单的水平偏移量。

*y*<br/>
中工作区坐标中快捷菜单的垂直偏移量

*pWndOwner*<br/>
中指向快捷菜单的父窗口的指针。

*bOwnMessage*<br/>
中指示消息路由方式的布尔参数。 如果*bOwnMessage*为 FALSE，则使用标准 MFC 路由。 否则， *pWndOwner*会接收消息。

*hmenuPopup*<br/>
中此方法将显示的菜单的句柄。

*bAutoDestroy*<br/>
中一个布尔参数，用于指示是否将自动销毁菜单。

*bRightAlign*<br/>
中布尔型参数，指示菜单项的对齐方式。 如果*bRightAlign*为 TRUE，则菜单为从右到左的读取顺序为右对齐。

### <a name="return-value"></a>返回值

如果方法成功显示菜单，则第一个方法重载将返回非零值;否则为0。 如果快捷菜单正确显示，则第二个方法重载返回指向[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)的指针;否则为 NULL。

### <a name="remarks"></a>备注

此方法类似于方法[CContextMenuManager：： TrackPopupMenu](#trackpopupmenu) ，因为这两个方法都显示一个快捷菜单。 但 `TrackPopupMenu` 返回选定菜单命令的索引。

如果参数*bAutoDestroy*为 FALSE，则必须手动调用继承的 `DestroyMenu` 方法来释放内存资源。 `ShowPopupMenu` 的默认实现不使用参数*bAutoDestroy*。 提供此方法是为了供将来使用，或者用于从 `CContextMenuManager` 类派生的自定义类。

##  <a name="trackpopupmenu"></a>CContextMenuManager：： TrackPopupMenu

显示指定的快捷菜单，并返回所选快捷菜单命令的索引。

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>parameters

*hmenuPopup*<br/>
中此方法显示的快捷菜单的句柄。

*x*<br/>
中工作区坐标中快捷菜单的水平偏移量。

*y*<br/>
中工作区坐标中快捷菜单的垂直偏移量。

*pWndOwner*<br/>
中指向快捷菜单的父窗口的指针。

*bRightAlign*<br/>
中指示菜单项的对齐方式的布尔参数。 如果*bRightAlign*为 TRUE，则菜单为从右到左的读取顺序为右对齐。 如果*bRightAlign*为 FALSE，则菜单为从左到右的读取顺序左对齐。

### <a name="return-value"></a>返回值

用户选择的命令的菜单命令 ID;如果用户在没有选择菜单命令的情况下关闭快捷菜单，则为0。

### <a name="remarks"></a>备注

此方法充当模式调用以显示快捷菜单。 在用户关闭快捷菜单或选择命令之前，应用程序将不会继续在代码中执行以下代码行。 可用于显示快捷菜单的另一种方法是 " [CContextMenuManager：： ShowPopupMenu](#showpopupmenu)"。 该方法不是模式调用，将不会返回所选命令的 ID。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)
