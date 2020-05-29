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
ms.openlocfilehash: c676355ebf44d6cc02bfa66ac870757627ae5a58
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754803"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager 类

对象`CContextMenuManager`管理快捷菜单，也称为上下文菜单。

## <a name="syntax"></a>语法

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CContext菜单管理器：C上下文菜单管理器](#ccontextmenumanager)|构造 `CContextMenuManager` 对象。|
|`CContextMenuManager::~CContextMenuManager`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CContext菜单管理器：：添加菜单](#addmenu)|添加新的快捷菜单。|
|[CContext菜单管理器：：获取菜单ById](#getmenubyid)|返回与提供的资源 ID 关联的菜单的句柄。|
|[CContext菜单管理器：：获取Menubyname](#getmenubyname)|返回与提供的菜单名称匹配的菜单的句柄。|
|[CContext菜单管理器：：获取菜单名称](#getmenunames)|返回菜单名称的列表。|
|[CContext菜单管理器：加载状态](#loadstate)|加载存储在 Windows 注册表中的快捷菜单。|
|[CContext菜单管理器：：重置状态](#resetstate)|从上下文菜单管理器清除快捷菜单。|
|[CContext菜单管理器：：保存状态](#savestate)|将快捷菜单保存到 Windows 注册表。|
|[CContext菜单管理器：：设置不关闭活动菜单](#setdontcloseactivemenu)|控制 在`CContextMenuManager`显示新快捷菜单时，是否关闭活动快捷菜单。|
|[CContext菜单管理器：：显示弹出菜单](#showpopupmenu)|显示指定的快捷菜单。|
|[CContext菜单管理器：：跟踪弹出菜单](#trackpopupmenu)|显示指定的快捷菜单。 返回所选菜单命令的索引。|

## <a name="remarks"></a>备注

`CContextMenuManager`管理快捷菜单并确保它们具有一致的外观。

不应手动创建`CContextMenuManager`对象。 应用程序的框架将创建对象`CContextMenuManager`。 但是，在初始化应用程序时，应调用[CWinAppEx：itContextMenuManager。](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) 初始化上下文管理器后，使用方法[CWinAppEx：：getContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)获取指向应用程序的上下文管理器的指针。

您可以通过调用`AddMenu`在运行时创建快捷菜单。 如果要在未首先接收用户输入的情况下显示菜单，请调用`ShowPopupMenu`。 `TrackPopupMenu`在要创建菜单并等待用户输入时使用。 `TrackPopupMenu`如果用户退出而不选择任何内容，则返回所选命令的索引或 0。

`CContextMenuManager`还可以将其状态保存并加载到 Windows 注册表。

## <a name="example"></a>示例

下面的示例演示如何向`CContextMenuManager`对象添加菜单，以及如何在`CContextMenuManager`对象显示新的弹出式菜单时不关闭活动弹出式菜单。 此代码段是[自定义页示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>要求

**标题：** afxcontextmenumanager.h

## <a name="ccontextmenumanageraddmenu"></a><a name="addmenu"></a>CContext菜单管理器：：添加菜单

向[CContextMenu管理器](../../mfc/reference/ccontextmenumanager-class.md)添加新的快捷菜单。

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>参数

*uiMenuNameResid*<br/>
[在]包含新菜单名称的字符串的资源 ID。

*uiMenuResId*<br/>
[在]菜单资源 ID。

*lpsz名称*<br/>
[在]包含新菜单名称的字符串。

### <a name="return-value"></a>返回值

如果方法成功，则非零;如果方法失败，为 0。

### <a name="remarks"></a>备注

如果*uiMenuResId*无效，或者同一名称的另一个菜单已在 中，`CContextMenuManager`则此方法将失败。

## <a name="ccontextmenumanagerccontextmenumanager"></a><a name="ccontextmenumanager"></a>CContext菜单管理器：C上下文菜单管理器

构造[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)对象。

```
CContextMenuManager();
```

### <a name="remarks"></a>备注

在大多数情况下，不应手动创建。 `CContextMenuManager` 应用程序的框架将创建对象`CContextMenuManager`。 您应该在应用程序的初始化期间调用[CWinAppEx：initContextMenuManager。](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) 要获取指向上下文管理器的指针，请致电[CWinAppEx：：获取ContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)。

## <a name="ccontextmenumanagergetmenubyid"></a><a name="getmenubyid"></a>CContext菜单管理器：：获取菜单ById

返回与给定资源 ID 关联的菜单的句柄。

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>参数

*恩梅努雷斯Id*<br/>
[在]菜单的资源 ID。

### <a name="return-value"></a>返回值

关联菜单的句柄或`NULL`找不到菜单。

## <a name="ccontextmenumanagergetmenubyname"></a><a name="getmenubyname"></a>CContext菜单管理器：：获取Menubyname

将句柄返回到特定菜单。

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
[在]包含要检索的菜单名称的字符串。

*普伊奥里格雷斯ID*<br/>
[出]指向 UINT 的指针。 此参数包含指定菜单的资源 ID（如果找到）。

### <a name="return-value"></a>返回值

与*lpszName*指定的名称匹配的菜单的句柄。 如果没有名为*lpszName*的菜单，则为 NULL。

### <a name="remarks"></a>备注

如果此方法找到与*lpszName*匹配的菜单`GetMenuByName`，则将菜单资源 ID 存储在参数*puiOrigResID*中。

## <a name="ccontextmenumanagergetmenunames"></a><a name="getmenunames"></a>CContext菜单管理器：：获取菜单名称

返回添加到[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)的菜单名称列表。

```cpp
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>参数

*名称列表*<br/>
[出]对[CStringList](../../mfc/reference/cstringlist-class.md)参数的引用。 此方法将菜单名称列表写入此参数。

## <a name="ccontextmenumanagerloadstate"></a><a name="loadstate"></a>CContext菜单管理器：加载状态

从 Windows 注册表加载与[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)关联的信息。

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]包含注册表项的相对路径的字符串。

### <a name="return-value"></a>返回值

如果方法成功，则非零;否则 0。

### <a name="remarks"></a>备注

*lpszProfileName*参数不是注册表项的绝对路径。 它是添加到应用程序的默认注册表项末尾的相对路径。 要获取或设置默认注册表项，请使用[CWinAppEx：：获取注册库](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx：：设置注册表项的方法](../../mfc/reference/cwinappex-class.md#setregistrybase)。

使用方法[CContextMenuManager：：保存状态](#savestate)以将快捷菜单保存到注册表。

## <a name="ccontextmenumanagerresetstate"></a><a name="resetstate"></a>CContext菜单管理器：：重置状态

清除与[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)关联的快捷菜单中的所有项。

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;如果发生故障，则 FALSE。

### <a name="remarks"></a>备注

此方法清除弹出式菜单并从 中删除`CContextMenuManager`它们。

## <a name="ccontextmenumanagersavestate"></a><a name="savestate"></a>CContext菜单管理器：：保存状态

将与[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)关联的信息保存到 Windows 注册表。

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]包含注册表项的相对路径的字符串。

### <a name="return-value"></a>返回值

如果方法成功，则非零;否则 0。

### <a name="remarks"></a>备注

*lpszProfileName*参数不是注册表项的绝对路径。 它是添加到应用程序的默认注册表项末尾的相对路径。 要获取或设置默认注册表项，请使用[CWinAppEx：：获取注册库](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx：：设置注册表项的方法](../../mfc/reference/cwinappex-class.md#setregistrybase)。

使用方法[CContextMenuManager：LoadState](#loadstate)从注册表加载快捷菜单。

## <a name="ccontextmenumanagersetdontcloseactivemenu"></a><a name="setdontcloseactivemenu"></a>CContext菜单管理器：：设置不关闭活动菜单

控制[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)在显示新的弹出式菜单时是否关闭活动弹出式菜单。

```cpp
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>参数

*bSet*<br/>
[在]控制是否关闭活动弹出菜单的布尔参数。 "TRUE"值表示活动弹出菜单未关闭。 FALSE 表示活动弹出窗口菜单已关闭。

### <a name="remarks"></a>备注

默认情况下，关闭`CContextMenuManager`活动弹出窗口菜单。

## <a name="ccontextmenumanagershowpopupmenu"></a><a name="showpopupmenu"></a>CContext菜单管理器：：显示弹出菜单

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

### <a name="parameters"></a>参数

*uiMenuResId*<br/>
[在]此方法将显示的菜单的资源 ID。

*x*<br/>
[在]客户端坐标中快捷菜单的水平偏移。

*Y*<br/>
[在]客户端坐标中快捷菜单的垂直偏移

*pwndOwner*<br/>
[在]指向快捷菜单的父窗口的指针。

*bown消息*<br/>
[在]指示消息路由方式的布尔参数。 如果*bown 消息*为 FALSE，则使用标准 MFC 路由。 否则 *，pWndOwner*会接收消息。

*赫梅努普*<br/>
[在]此方法将显示的菜单的句柄。

*bAuto销毁*<br/>
[在]指示菜单是否将自动销毁的布尔参数。

*b 右对齐*<br/>
[在]指示菜单项对齐方式的布尔参数。 如果*bRight对齐*为 TRUE，则菜单在从右到左读取顺序时右对齐。

### <a name="return-value"></a>返回值

如果该方法成功显示菜单，则第一个方法重载将返回非零;否则 0。 如果快捷菜单显示正确，则第二个方法重载返回指向[CMFCPopupMenu 的](../../mfc/reference/cmfcpopupmenu-class.md)指针;否则 NULL。

### <a name="remarks"></a>备注

此方法类似于方法[CContextMenuManager：：TrackPopupMenu，](#trackpopupmenu)因为两种方法都显示一个快捷菜单。 但是，`TrackPopupMenu`返回所选菜单命令的索引。

如果参数*bAuto销毁*是 FALSE，则必须手动调用继承`DestroyMenu`的方法来释放内存资源。 的`ShowPopupMenu`默认实现不使用参数*bAuto销毁*。 它供将来使用或用于从类派生的`CContextMenuManager`自定义类。

## <a name="ccontextmenumanagertrackpopupmenu"></a><a name="trackpopupmenu"></a>CContext菜单管理器：：跟踪弹出菜单

显示指定的快捷菜单并返回所选快捷菜单命令的索引。

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>参数

*赫梅努普*<br/>
[在]此方法显示的快捷菜单的句柄。

*x*<br/>
[在]客户端坐标中快捷菜单的水平偏移。

*Y*<br/>
[在]客户端坐标中快捷菜单的垂直偏移。

*pwndOwner*<br/>
[在]指向快捷菜单的父窗口的指针。

*b 右对齐*<br/>
[在]指示菜单项对齐方式的布尔参数。 如果*bRight对齐*为 TRUE，则菜单在从右到左读取顺序时右对齐。 如果*bRightAlign*为 FALSE，则菜单在从左到右的阅读顺序中左对齐。

### <a name="return-value"></a>返回值

用户选择的命令的菜单命令 ID;如果用户在不选择菜单命令的情况下关闭快捷菜单，则为 0。

### <a name="remarks"></a>备注

此方法用作显示快捷菜单的模态调用。 在用户关闭快捷菜单或选择命令之前，应用程序不会继续到代码中的下一行。 可用于显示快捷菜单的替代方法是[CContextMenuManager：：ShowPopupMenu](#showpopupmenu)。 该方法不是模态调用，不会返回所选命令的 ID。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)
