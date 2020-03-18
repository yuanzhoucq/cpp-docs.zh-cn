---
title: CMenu 类
ms.date: 11/04/2016
f1_keywords:
- CMenu
- AFXWIN/CMenu
- AFXWIN/CMenu::CMenu
- AFXWIN/CMenu::AppendMenu
- AFXWIN/CMenu::Attach
- AFXWIN/CMenu::CheckMenuItem
- AFXWIN/CMenu::CheckMenuRadioItem
- AFXWIN/CMenu::CreateMenu
- AFXWIN/CMenu::CreatePopupMenu
- AFXWIN/CMenu::DeleteMenu
- AFXWIN/CMenu::DeleteTempMap
- AFXWIN/CMenu::DestroyMenu
- AFXWIN/CMenu::Detach
- AFXWIN/CMenu::DrawItem
- AFXWIN/CMenu::EnableMenuItem
- AFXWIN/CMenu::FromHandle
- AFXWIN/CMenu::GetDefaultItem
- AFXWIN/CMenu::GetMenuContextHelpId
- AFXWIN/CMenu::GetMenuInfo
- AFXWIN/CMenu::GetMenuItemCount
- AFXWIN/CMenu::GetMenuItemID
- AFXWIN/CMenu::GetMenuItemInfo
- AFXWIN/CMenu::GetMenuState
- AFXWIN/CMenu::GetMenuString
- AFXWIN/CMenu::GetSafeHmenu
- AFXWIN/CMenu::GetSubMenu
- AFXWIN/CMenu::InsertMenu
- AFXWIN/CMenu::InsertMenuItem
- AFXWIN/CMenu::LoadMenu
- AFXWIN/CMenu::LoadMenuIndirect
- AFXWIN/CMenu::MeasureItem
- AFXWIN/CMenu::ModifyMenu
- AFXWIN/CMenu::RemoveMenu
- AFXWIN/CMenu::SetDefaultItem
- AFXWIN/CMenu::SetMenuContextHelpId
- AFXWIN/CMenu::SetMenuInfo
- AFXWIN/CMenu::SetMenuItemBitmaps
- AFXWIN/CMenu::SetMenuItemInfo
- AFXWIN/CMenu::TrackPopupMenu
- AFXWIN/CMenu::TrackPopupMenuEx
- AFXWIN/CMenu::m_hMenu
helpviewer_keywords:
- CMenu [MFC], CMenu
- CMenu [MFC], AppendMenu
- CMenu [MFC], Attach
- CMenu [MFC], CheckMenuItem
- CMenu [MFC], CheckMenuRadioItem
- CMenu [MFC], CreateMenu
- CMenu [MFC], CreatePopupMenu
- CMenu [MFC], DeleteMenu
- CMenu [MFC], DeleteTempMap
- CMenu [MFC], DestroyMenu
- CMenu [MFC], Detach
- CMenu [MFC], DrawItem
- CMenu [MFC], EnableMenuItem
- CMenu [MFC], FromHandle
- CMenu [MFC], GetDefaultItem
- CMenu [MFC], GetMenuContextHelpId
- CMenu [MFC], GetMenuInfo
- CMenu [MFC], GetMenuItemCount
- CMenu [MFC], GetMenuItemID
- CMenu [MFC], GetMenuItemInfo
- CMenu [MFC], GetMenuState
- CMenu [MFC], GetMenuString
- CMenu [MFC], GetSafeHmenu
- CMenu [MFC], GetSubMenu
- CMenu [MFC], InsertMenu
- CMenu [MFC], InsertMenuItem
- CMenu [MFC], LoadMenu
- CMenu [MFC], LoadMenuIndirect
- CMenu [MFC], MeasureItem
- CMenu [MFC], ModifyMenu
- CMenu [MFC], RemoveMenu
- CMenu [MFC], SetDefaultItem
- CMenu [MFC], SetMenuContextHelpId
- CMenu [MFC], SetMenuInfo
- CMenu [MFC], SetMenuItemBitmaps
- CMenu [MFC], SetMenuItemInfo
- CMenu [MFC], TrackPopupMenu
- CMenu [MFC], TrackPopupMenuEx
- CMenu [MFC], m_hMenu
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
ms.openlocfilehash: 1cd7be72dc6c9a38fae4f5ccc1a15c184a2d4466
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426239"
---
# <a name="cmenu-class"></a>CMenu 类

封装 Windows `HMENU`。

## <a name="syntax"></a>语法

```
class CMenu : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMenu：： CMenu](#cmenu)|构造 `CMenu` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|在此菜单的末尾追加一个新项。|
|[CMenu：： Attach](#attach)|将 Windows 菜单句柄附加到 `CMenu` 的对象。|
|[CMenu：： CheckMenuItem](#checkmenuitem)|在弹出菜单中的菜单项旁边选中或删除复选标记。|
|[CMenu：： CheckMenuRadioItem](#checkmenuradioitem)|将单选按钮置于菜单项旁边，并从该组中的所有其他菜单项中删除该单选按钮。|
|[CMenu：： CreateMenu](#createmenu)|创建一个空菜单，并将其附加到 `CMenu` 对象上。|
|[CMenu：： CreatePopupMenu](#createpopupmenu)|创建一个空的弹出菜单，并将其附加到 `CMenu` 对象上。|
|[CMenu：:D eleteMenu](#deletemenu)|从菜单中删除指定项。 如果菜单项具有关联的弹出菜单，则会销毁弹出菜单的句柄，并释放它所使用的内存。|
|[CMenu：:D eleteTempMap](#deletetempmap)|删除 `FromHandle` 成员函数创建的任何临时 `CMenu` 对象。|
|[CMenu：:D estroyMenu](#destroymenu)|销毁附加到 `CMenu` 对象的菜单，并释放菜单占用的任何内存。|
|[CMenu：:D etach](#detach)|从 `CMenu` 对象分离一个 Windows 菜单句柄并返回该句柄。|
|[CMenu：:D rawItem](#drawitem)|当所有者描述的菜单的视觉方面发生变化时，由框架调用。|
|[CMenu：： EnableMenuItem](#enablemenuitem)|启用、禁用或暗显菜单项。|
|[CMenu：： FromHandle](#fromhandle)|返回一个指向给定 Windows 菜单句柄的 `CMenu` 对象的指针。|
|[CMenu：： GetDefaultItem](#getdefaultitem)|确定指定菜单上的默认菜单项。|
|[CMenu：： GetMenuContextHelpId](#getmenucontexthelpid)|检索与菜单关联的帮助上下文 ID。|
|[CMenu：： GetMenuInfo](#getmenuinfo)|检索特定菜单上的信息。|
|[CMenu：： GetMenuItemCount](#getmenuitemcount)|确定弹出菜单或顶级菜单中项的数目。|
|[CMenu：： GetMenuItemID](#getmenuitemid)|获取位于指定位置的菜单项的菜单项标识符。|
|[CMenu：： GetMenuItemInfo](#getmenuiteminfo)|检索有关菜单项的信息。|
|[CMenu：： GetMenuState](#getmenustate)|返回指定菜单项的状态或弹出菜单中的项数。|
|[CMenu：： GetMenuString](#getmenustring)|检索指定菜单项的标签。|
|[CMenu：： GetSafeHmenu](#getsafehmenu)|返回由此 `CMenu` 对象包装的 `m_hMenu`。|
|[CMenu：： GetSubMenu](#getsubmenu)|检索指向弹出菜单的指针。|
|[CMenu::InsertMenu](#insertmenu)|在指定位置插入新菜单项，在菜单中向下移动其他项。|
|[CMenu：： InsertMenuItem](#insertmenuitem)|在菜单中的指定位置插入新菜单项。|
|[CMenu：： LoadMenu](#loadmenu)|从可执行文件加载菜单资源，并将其附加到 `CMenu` 的对象。|
|[CMenu：： LoadMenuIndirect](#loadmenuindirect)|从内存中的菜单模板加载菜单，并将其附加到 `CMenu` 对象上。|
|[CMenu：： MeasureItem](#measureitem)|在创建所有者描述的菜单时由框架调用，以确定菜单的尺寸。|
|[CMenu::ModifyMenu](#modifymenu)|更改指定位置的现有菜单项。|
|[CMenu：： RemoveMenu](#removemenu)|删除具有指定菜单中的关联弹出菜单的菜单项。|
|[CMenu：： SetDefaultItem](#setdefaultitem)|设置指定菜单的默认菜单项。|
|[CMenu：： SetMenuContextHelpId](#setmenucontexthelpid)|设置要与菜单关联的帮助上下文 ID。|
|[CMenu：： SetMenuInfo](#setmenuinfo)|设置特定菜单上的信息。|
|[CMenu：： SetMenuItemBitmaps](#setmenuitembitmaps)|将指定的选中标记位图与菜单项相关联。|
|[CMenu：： SetMenuItemInfo](#setmenuiteminfo)|更改有关菜单项的信息。|
|[CMenu：： TrackPopupMenu](#trackpopupmenu)|在指定位置显示一个浮动的弹出菜单，并在弹出菜单上跟踪项的选定内容。|
|[CMenu：： TrackPopupMenuEx](#trackpopupmenuex)|在指定位置显示一个浮动的弹出菜单，并在弹出菜单上跟踪项的选定内容。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[CMenu：： operator HMENU](#operator_hmenu)|检索 menu 对象的句柄。|
|[CMenu：： operator！ =](#operator_neq)|确定两个菜单对象是否不相等。|
|[CMenu：： operator = =](#operator_eq_eq)|确定两个菜单对象是否相等。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CMenu：： m_hMenu](#m_hmenu)|指定附加到 `CMenu` 对象的 Windows 菜单的句柄。|

## <a name="remarks"></a>备注

它提供用于创建、跟踪、更新和销毁菜单的成员函数。

将堆栈帧上的 `CMenu` 对象创建为本地对象，然后根据需要调用 `CMenu`的成员函数来操作新菜单。 接下来，调用[CWnd：： SetMenu](../../mfc/reference/cwnd-class.md#setmenu)将菜单设置为窗口，然后立即调用 `CMenu` 对象的[分离](#detach)成员函数。 `CWnd::SetMenu` 成员函数将窗口的菜单设置为新菜单，导致重绘窗口以反映菜单更改，同时还将菜单的所有权传递给窗口。 对 `Detach` 的调用将从 `CMenu` 对象分离 HMENU，以便当本地 `CMenu` 变量超出范围时，`CMenu` 对象析构函数不会尝试销毁它不再拥有的菜单。 销毁窗口时，菜单本身会自动销毁。

您可以使用[LoadMenuIndirect](#loadmenuindirect)成员函数从内存中的模板创建一个菜单，但通过调用[LoadMenu](#loadmenu)从资源创建的菜单更易于维护，并且菜单资源本身可以通过菜单编辑器来创建和修改。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="appendmenu"></a>CMenu：： AppendMenu

将新项追加到菜单的末尾。

```
BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>parameters

*nFlags*<br/>
指定在将新菜单项添加到菜单时该菜单项的状态信息。 它包含 "备注" 部分中列出的一个或多个值。

*nIDNewItem*<br/>
指定新菜单项的命令 ID，或者，如果*nFlags*设置为 MF_POPUP，则为弹出菜单的菜单控点（`HMENU`）。 如果*nFlags*设置为 MF_SEPARATOR，则忽略*nIDNewItem*参数（不需要）。

*lpszNewItem*<br/>
指定新菜单项的内容。 *NFlags*参数用于按以下方式解释*lpszNewItem* ：

|nFlags|LpszNewItem 的解释|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含应用程序提供的32位值，应用程序可使用该值来维护与菜单项关联的附加数据。 当应用程序处理 WM_MEASUREITEM 和 WM_DRAWITEM 消息时，此32位值可用于应用程序。 该值存储在与这些消息一起提供的结构的 `itemData` 成员中。|
|MF_STRING|包含指向以 null 结尾的字符串的指针。 这是默认的解释。|
|MF_SEPARATOR|忽略*lpszNewItem*参数（不需要）。|

*.Pbmp*<br/>
指向将用作菜单项的 `CBitmap` 对象。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

应用程序可以通过在*nFlags*中设置值来指定菜单项的状态。 当*nIDNewItem*指定一个弹出菜单时，它将成为它要追加到的菜单的一部分。 如果该菜单被销毁，则追加的菜单也会被销毁。 追加的菜单应该与 `CMenu` 对象分离，以避免冲突。 请注意，MF_STRING 和 MF_OWNERDRAW 对于 `AppendMenu`的位图版本无效。

以下列表描述了可在*nFlags*中设置的标志：

- MF_CHECKED 作为 MF_UNCHECKED 的切换，以将默认复选标记置于该项旁边。 当应用程序提供了检查标记位图（请参阅[SetMenuItemBitmaps](#setmenuitembitmaps)成员函数）时，将显示 "选中标记" 位图。

- MF_UNCHECKED 使用 MF_CHECKED 进行切换，以便删除项旁边的复选标记。 当应用程序提供了检查标记位图（请参阅 `SetMenuItemBitmaps` 成员函数）时，将显示 "勾号 off" 位图。

- MF_DISABLED 禁用菜单项，使其不能被选中但不会使其变暗。

- MF_ENABLED 启用菜单项，以便可以选择它并将其还原为灰显状态。

- MF_GRAYED 禁用菜单项，使其不能被选中并使其变暗。

- MF_MENUBARBREAK 将项放置在静态菜单或弹出菜单中新列中的新行上。 新的弹出菜单列将通过垂直分隔线与旧列分隔开。

- MF_MENUBREAK 将项放置在静态菜单或弹出菜单中新列中的新行上。 不在列之间放置分隔线。

- MF_OWNERDRAW 指定该项是所有者描述项。 当首次显示菜单时，拥有菜单的窗口将收到 WM_MEASUREITEM 消息，该消息将检索菜单项的高度和宽度。 WM_DRAWITEM 消息是指每当所有者必须更新菜单项的视觉外观时发送的消息。 此选项对于顶级菜单项无效。

- MF_POPUP 指定菜单项具有与之关联的弹出菜单。 ID 参数指定要与项关联的弹出菜单的句柄。 这用于向弹出菜单项添加顶级弹出菜单或层次结构弹出菜单的菜单项。

- MF_SEPARATOR 绘制水平分隔线。 只能在弹出菜单中使用。 此行不能为灰显、禁用或突出显示。 其他参数将被忽略。

- MF_STRING 指定菜单项是一个字符串。

以下每个组都列出了互相排斥并且不能一起使用的标志：

- MF_DISABLED、MF_ENABLED 和 MF_GRAYED

- MF_STRING、MF_OWNERDRAW、MF_SEPARATOR 和位图版本

- MF_MENUBARBREAK 和 MF_MENUBREAK

- MF_CHECKED 和 MF_UNCHECKED

每当窗口中的菜单发生更改（无论是否显示窗口）时，应用程序应调用[CWnd：:D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar)。

### <a name="example"></a>示例

  请参阅[CMenu：： CreateMenu](#createmenu)的示例。

##  <a name="attach"></a>CMenu：： Attach

将现有的 Windows 菜单附加到 `CMenu` 的对象。

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>parameters

*hMenu*<br/>
指定 Windows 菜单的句柄。

### <a name="return-value"></a>返回值

如果操作成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果菜单已附加到 `CMenu` 对象，则不应调用此函数。 菜单句柄存储在 `m_hMenu` 数据成员中。

如果您要操作的菜单已经与窗口相关联，则可以使用[CWnd：： GetMenu](../../mfc/reference/cwnd-class.md#getmenu)函数获取菜单的句柄。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="checkmenuitem"></a>CMenu：： CheckMenuItem

向弹出菜单中的菜单项添加或删除复选标记。

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>parameters

*nIDCheckItem*<br/>
指定要检查的菜单项，由*n*确定。

*n*<br/>
指定如何检查菜单项以及如何确定项在菜单中的位置。 *N*参数可以是 MF_CHECKED 或 MF_UNCHECKED 与 MF_BYPOSITION 或 MF_BYCOMMAND 标志的组合。 可以使用按位 "或" 运算符组合这些标志。 它们具有以下含义：

- MF_BYCOMMAND 指定参数提供现有菜单项的命令 ID。 这是默认值。

- MF_BYPOSITION 指定参数提供现有菜单项的位置。 第一项的位置为0。

- MF_CHECKED 作为 MF_UNCHECKED 的切换，以将默认复选标记置于该项旁边。

- MF_UNCHECKED 使用 MF_CHECKED 进行切换，以便删除项旁边的复选标记。

### <a name="return-value"></a>返回值

项的前一状态为： MF_CHECKED 或 MF_UNCHECKED，如果菜单项不存在，则为0xFFFFFFFF。

### <a name="remarks"></a>备注

*NIDCheckItem*参数指定要修改的项。

*NIDCheckItem*参数可以标识弹出菜单项和菜单项。 不需要执行任何特殊步骤即可检查弹出菜单项。 不能检查顶级菜单项。 必须按位置检查弹出菜单项，因为它没有关联的菜单项标识符。

### <a name="example"></a>示例

  请参阅[CMenu：： GetMenuState](#getmenustate)的示例。

##  <a name="checkmenuradioitem"></a>CMenu：： CheckMenuRadioItem

检查指定的菜单项并使其成为单选项。

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>parameters

*nIDFirst*<br/>
指定（根据*nFlags*的值）单选按钮组中的第一个菜单项。

*nIDLast*<br/>
指定（根据*nFlags*的值）单选按钮组中的最后一个菜单项。

*nIDItem*<br/>
将（根据*nFlags*的值）指定为将使用单选按钮进行检查的组中的项。

*nFlags*<br/>
按以下方式指定*nIDFirst*、 *nIDLast*和*nIDItem*的解释：

|nFlags|解释|
|------------|--------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 均未设置，则此值为默认值。|
|MF_BYPOSITION|指定参数提供现有菜单项的位置。 第一项的位置为0。|

### <a name="return-value"></a>返回值

如果成功，则为非零值;否则为0

### <a name="remarks"></a>备注

同时，该函数取消选中关联组中的所有其他菜单项，并清除这些项的单选项类型标志。 使用单选按钮（或项目符号）位图而不是选中标记位图显示选中的项。

### <a name="example"></a>示例

  请参阅[ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range)的示例。

##  <a name="cmenu"></a>CMenu：： CMenu

创建一个空菜单，并将其附加到 `CMenu` 对象上。

```
CMenu();
```

### <a name="remarks"></a>备注

在调用 `CMenu:` 的 create 或 load 成员函数之一之前，不会创建菜单。

- [CreateMenu](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [附加](#attach)

##  <a name="createmenu"></a>CMenu：： CreateMenu

创建一个菜单，并将其附加到 `CMenu` 对象上。

```
BOOL CreateMenu();
```

### <a name="return-value"></a>返回值

如果成功创建菜单，则为非零值;否则为0。

### <a name="remarks"></a>备注

菜单最初为空。 可以通过使用 `AppendMenu` 或 `InsertMenu` 成员函数来添加菜单项。

如果将菜单分配给窗口，则当窗口被销毁时自动销毁。

在退出之前，如果未将菜单分配给窗口，应用程序必须释放与菜单关联的系统资源。 应用程序通过调用[DestroyMenu](#destroymenu)成员函数来释放菜单。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

##  <a name="createpopupmenu"></a>CMenu：： CreatePopupMenu

创建一个弹出菜单，并将其附加到 `CMenu` 对象上。

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>返回值

如果成功创建了弹出菜单，则为非零值;否则为0。

### <a name="remarks"></a>备注

菜单最初为空。 可以通过使用 `AppendMenu` 或 `InsertMenu` 成员函数来添加菜单项。 应用程序可以将弹出菜单添加到现有菜单或弹出菜单。 `TrackPopupMenu` 成员函数可用于将此菜单显示为浮动的弹出菜单并跟踪弹出菜单上的选项。

如果将菜单分配给窗口，则当窗口被销毁时自动销毁。 如果将菜单添加到现有菜单，该菜单在销毁后会自动销毁。

在退出之前，如果未将菜单分配给窗口，应用程序必须释放与弹出菜单关联的系统资源。 应用程序通过调用[DestroyMenu](#destroymenu)成员函数来释放菜单。

### <a name="example"></a>示例

  请参阅[CMenu：： CreateMenu](#createmenu)的示例。

##  <a name="deletemenu"></a>CMenu：:D eleteMenu

从菜单中删除一项。

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>parameters

*位置*<br/>
指定要删除的菜单项，由*nFlags*确定。

*nFlags*<br/>
用于按以下方式解释*位置*：

|nFlags|位置的解释|
|------------|---------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 均未设置，则此值为默认值。|
|MF_BYPOSITION|指定参数提供现有菜单项的位置。 第一项的位置为0。|

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

如果菜单项具有关联的弹出菜单，`DeleteMenu` 会销毁弹出菜单的句柄，并释放弹出菜单使用的内存。

每当窗口中的菜单发生更改（无论是否显示窗口）时，应用程序必须调用[CWnd：:D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar)。

### <a name="example"></a>示例

  请参阅[CWnd：： GetMenu](../../mfc/reference/cwnd-class.md#getmenu)的示例。

##  <a name="deletetempmap"></a>CMenu：:D eleteTempMap

由 `CWinApp` 空闲时间处理程序自动调用，将删除[FromHandle](#fromhandle)成员函数创建的所有临时 `CMenu` 对象。

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>备注

`DeleteTempMap` 在删除 `CMenu` 对象之前，分离附加到临时 `CMenu` 对象的 Windows 菜单对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

##  <a name="destroymenu"></a>CMenu：:D estroyMenu

销毁菜单以及使用的任何 Windows 资源。

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>返回值

如果菜单被销毁，则为非零值;否则为0。

### <a name="remarks"></a>备注

菜单在销毁之前从 `CMenu` 对象分离。 Windows `DestroyMenu` 函数在 `CMenu` 析构函数中自动调用。

### <a name="example"></a>示例

  请参阅[CMenu：： CreateMenu](#createmenu)的示例。

##  <a name="detach"></a>CMenu：:D etach

从 `CMenu` 对象分离一个 Windows 菜单并返回该句柄。

```
HMENU Detach();
```

### <a name="return-value"></a>返回值

如果成功，则为 Windows 菜单的 HMENU 类型的句柄;否则为 NULL。

### <a name="remarks"></a>备注

`m_hMenu` 数据成员设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="drawitem"></a>CMenu：:D rawItem

当所有者描述的菜单的视觉方面发生变化时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>parameters

*lpDrawItemStruct*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的指针，该结构包含所需绘图类型的相关信息。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT` 结构的 `itemAction` 成员定义要执行的绘图操作。 重写此成员函数以实现 `CMenu` 对象的所有者描述的绘图。 应用程序应还原在此成员函数终止之前为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口（GDI）对象。

有关 `DRAWITEMSTRUCT` 结构的说明，请参阅[CWnd：： OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) 。

### <a name="example"></a>示例

以下代码来自 MFC [CTRLTEST](../../overview/visual-cpp-samples.md)示例：

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

##  <a name="enablemenuitem"></a>CMenu：： EnableMenuItem

启用、禁用或变暗菜单项。

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>parameters

*nIDEnableItem*<br/>
指定要启用的菜单项，由*nEnable*确定。 此参数可以指定弹出菜单项以及标准菜单项。

*nEnable*<br/>
指定要执行的操作。 它可以是 MF_DISABLED、MF_ENABLED 或 MF_GRAYED 与 MF_BYCOMMAND 或 MF_BYPOSITION 的组合。 可以使用按位 "或" 运算符组合这些值。 这些值将具有以下含义：

- MF_BYCOMMAND 指定参数提供现有菜单项的命令 ID。 这是默认值。

- MF_BYPOSITION 指定参数提供现有菜单项的位置。 第一项的位置为0。

- MF_DISABLED 禁用菜单项，使其不能被选中但不会使其变暗。

- MF_ENABLED 启用菜单项，以便可以选择它并将其还原为灰显状态。

- MF_GRAYED 禁用菜单项，使其不能被选中并使其变暗。

### <a name="return-value"></a>返回值

以前的状态（MF_DISABLED、MF_ENABLED 或 MF_GRAYED）或-1 （如果无效）。

### <a name="remarks"></a>备注

[CreateMenu](#createmenu)、 [InsertMenu](#insertmenu)、 [ModifyMenu](#modifymenu)和[LoadMenuIndirect](#loadmenuindirect)成员函数还可以设置菜单项的状态（启用、禁用或灰显）。

使用 MF_BYPOSITION 值需要应用程序使用正确的 `CMenu`。 如果使用菜单栏的 `CMenu`，则顶级菜单项（菜单栏中的项）会受到影响。 若要按位置设置弹出窗口或嵌套的弹出菜单中项的状态，应用程序必须指定弹出菜单的 `CMenu`。

当应用程序指定 MF_BYCOMMAND 标志时，Windows 将检查从属于 `CMenu`的所有弹出菜单项;因此，除非存在重复的菜单项，否则使用菜单栏 `CMenu` 就足够了。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

##  <a name="fromhandle"></a>CMenu：： FromHandle

返回一个指向 `CMenu` 对象的指针，该指针给定了菜单的 Windows 句柄。

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>parameters

*hMenu*<br/>
菜单的 Windows 句柄。

### <a name="return-value"></a>返回值

指向可能是临时或永久的 `CMenu` 的指针。

### <a name="remarks"></a>备注

如果 `CMenu` 对象尚未附加到 Windows menu 对象，则将创建一个临时的 `CMenu` 对象并将其附加。

只有在下一次应用程序在其事件循环中有空闲时间（此时删除所有临时对象）时，此临时 `CMenu` 对象才有效。

### <a name="example"></a>示例

  请参阅[CMenu：： CreateMenu](#createmenu)的示例。

##  <a name="getdefaultitem"></a>CMenu：： GetDefaultItem

确定指定菜单上的默认菜单项。

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>parameters

*gmdiFlags*<br/>
指定函数搜索菜单项的方式的值。 此参数可以是 "无"、一个或以下值的组合：

|值|含义|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|指定如果默认项是打开子菜单的项，则该函数将以递归方式在相应的子菜单中进行搜索。 如果子菜单没有默认项，则返回值标识打开子菜单的项。<br /><br /> 默认情况下，函数返回指定菜单上的第一个默认项，而不考虑它是否是打开子菜单的项。|
|GMDI_USEDISABLED|指定该函数将返回默认项，即使已禁用。<br /><br /> 默认情况下，该函数跳过禁用或灰色项。|

*fByPos*<br/>
指定是否检索菜单项的标识符或其位置的值。 如果此参数为 FALSE，则返回标识符。 否则，将返回位置。

### <a name="return-value"></a>返回值

如果函数成功，则返回值为菜单项的标识符或位置。 如果函数失败，则返回值为-1。

### <a name="remarks"></a>备注

此成员函数实现 Win32 函数[GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

  请参阅[CMenu：： InsertMenu](#insertmenu)的示例。

##  <a name="getmenucontexthelpid"></a>CMenu：： GetMenuContextHelpId

检索与 `CMenu`关联的上下文帮助 ID。

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>返回值

当前与 `CMenu` 关联的上下文帮助 ID （如果有）;否则为零。

### <a name="example"></a>示例

  请参阅[CMenu：： InsertMenu](#insertmenu)的示例。

##  <a name="getmenuinfo"></a>CMenu：： GetMenuInfo

检索菜单的信息。

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>parameters

*lpcmi*<br/>
指向[MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo)结构的指针，该结构包含菜单的信息。

### <a name="return-value"></a>返回值

如果函数成功，则返回值为非零值;否则，返回值为零。

### <a name="remarks"></a>备注

调用此函数可检索有关菜单的信息。

##  <a name="getmenuitemcount"></a>CMenu：： GetMenuItemCount

确定弹出菜单或顶级菜单中项的数目。

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>返回值

如果函数成功，则为菜单中项的数量;否则为-1。

### <a name="example"></a>示例

  请参阅[CWnd：： GetMenu](../../mfc/reference/cwnd-class.md#getmenu)的示例。

##  <a name="getmenuitemid"></a>CMenu：： GetMenuItemID

获取位于由*nPos*定义的位置的菜单项的菜单项标识符。

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>parameters

*nPos*<br/>
指定要检索其 ID 的菜单项的位置（从零开始）。

### <a name="return-value"></a>返回值

如果函数成功，则为弹出菜单中指定项的项 ID。 如果指定的项是一个弹出菜单（而不是弹出菜单中的项），则返回值为-1。 如果*nPos*对应于一个分隔符菜单项，则返回值为0。

### <a name="example"></a>示例

  请参阅[CMenu：： InsertMenu](#insertmenu)的示例。

##  <a name="getmenuiteminfo"></a>CMenu：： GetMenuItemInfo

检索有关菜单项的信息。

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>parameters

*uItem*<br/>
要获取其相关信息的菜单项的标识符或位置。 此参数的意义取决于 `ByPos`的值。

*lpMenuItemInfo*<br/>
指向[MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow)的指针，如 Windows SDK 中所述，其中包含有关菜单的信息。

*fByPos*<br/>
指定 `nIDItem`含义的值。 默认情况下，`ByPos` 为 FALSE，表示 uItem 是菜单项标识符。 如果 `ByPos` 未设置为 FALSE，则指示菜单项位置。

### <a name="return-value"></a>返回值

如果该函数成功，则返回值为非零值。 如果函数失败，则返回值为零。 若要获取更详细的错误信息，请使用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)，如 Windows SDK 中所述。

### <a name="remarks"></a>备注

此成员函数实现 Win32 函数[GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow)的行为，如 Windows SDK 中所述。 请注意，在 `GetMenuItemInfo`的 MFC 实现中，不使用菜单的句柄。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

##  <a name="getmenustate"></a>CMenu：： GetMenuState

返回指定菜单项的状态或弹出菜单中的项数。

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>parameters

*nID*<br/>
指定由*nFlags*确定的菜单项 ID。

*nFlags*<br/>
指定*nID*的性质。 可以为下列值之一：

- MF_BYCOMMAND 指定参数提供现有菜单项的命令 ID。 这是默认值。

- MF_BYPOSITION 指定参数提供现有菜单项的位置。 第一项的位置为0。

### <a name="return-value"></a>返回值

如果指定的项不存在，则值为0xFFFFFFFF。 如果*nId*标识一个弹出菜单，则高序位字节包含弹出菜单中的项数，而低序位字节包含与弹出菜单相关联的菜单标志。 否则，返回值为以下列表中值的掩码（布尔值或）（此掩码描述*nId*标识的菜单项的状态）：

- MF_CHECKED 作为 MF_UNCHECKED 的切换，以将默认复选标记置于该项旁边。 当应用程序提供了检查标记位图（请参阅 "`SetMenuItemBitmaps`" 成员函数）时，将显示 "选中标记" 位图。

- MF_DISABLED 禁用菜单项，使其不能被选中但不会使其变暗。

- MF_ENABLED 启用菜单项，以便可以选择它并将其还原为灰显状态。 请注意，此常量的值为 0;使用此值时，应用程序不应对0进行测试。

- MF_GRAYED 禁用菜单项，使其不能被选中并使其变暗。

- MF_MENUBARBREAK 将项放置在静态菜单或弹出菜单中新列中的新行上。 新的弹出菜单列将通过垂直分隔线与旧列分隔开。

- MF_MENUBREAK 将项放置在静态菜单或弹出菜单中新列中的新行上。 不在列之间放置分隔线。

- MF_SEPARATOR 绘制水平分隔线。 只能在弹出菜单中使用。 此行不能为灰显、禁用或突出显示。 其他参数将被忽略。

- MF_UNCHECKED 使用 MF_CHECKED 进行切换，以便删除项旁边的复选标记。 当应用程序提供了检查标记位图（请参阅 `SetMenuItemBitmaps` 成员函数）时，将显示 "勾号 off" 位图。 请注意，此常量的值为 0;使用此值时，应用程序不应对0进行测试。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

##  <a name="getmenustring"></a>CMenu：： GetMenuString

将指定菜单项的标签复制到指定缓冲区。

```
int GetMenuString(
    UINT nIDItem,
    LPTSTR lpString,
    int nMaxCount,
    UINT nFlags) const;

int GetMenuString(
    UINT nIDItem,
    CString& rString,
    UINT nFlags) const;
```

### <a name="parameters"></a>parameters

*nIDItem*<br/>
指定菜单项的整数标识符或菜单中菜单项的偏移量，具体取决于*nFlags*的值。

*lpString*<br/>
指向接收标签的缓冲区。

*rString*<br/>
对 `CString` 对象的引用，该对象将接收复制的菜单字符串。

*nMaxCount*<br/>
指定要复制的标签的最大长度（以字符为字符）。 如果标签的长度超过在*nMaxCount*中指定的最大值，则会截断额外的字符。

*nFlags*<br/>
指定*nIDItem*参数的解释。 可以为下列值之一：

|nFlags|NIDItem 的解释|
|------------|-------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 均未设置，则此值为默认值。|
|MF_BYPOSITION|指定参数提供现有菜单项的位置。 第一项的位置为0。|

### <a name="return-value"></a>返回值

指定复制到缓冲区的实际字符数，不包括 null 终止符。

### <a name="remarks"></a>备注

*NMaxCount*参数应比标签中的字符数大一，以容纳终止字符串的 null 字符。

### <a name="example"></a>示例

  请参阅[CMenu：： InsertMenu](#insertmenu)的示例。

##  <a name="getsafehmenu"></a>CMenu：： GetSafeHmenu

返回由此 `CMenu` 对象包装的 HMENU 或 NULL`CMenu` 指针。

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>示例

  请参阅[CMenu：： LoadMenu](#loadmenu)的示例。

##  <a name="getsubmenu"></a>CMenu：： GetSubMenu

检索弹出菜单的 `CMenu` 对象。

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>parameters

*nPos*<br/>
指定菜单中包含的弹出菜单的位置。 对于第一个菜单项，位置值从0开始。 此函数中不能使用弹出菜单的标识符。

### <a name="return-value"></a>返回值

指向 `CMenu` 对象的指针，该对象的 `m_hMenu` 成员包含弹出菜单的句柄（如果出现在给定位置的弹出菜单）;否则为 NULL。 如果 `CMenu` 对象不存在，则创建一个临时对象。 不应存储返回的 `CMenu` 指针。

### <a name="example"></a>示例

  请参阅[CMenu：： TrackPopupMenu](#trackpopupmenu)的示例。

##  <a name="insertmenu"></a>CMenu：： InsertMenu

在*位置*指定的位置插入一个新的菜单项，并在菜单中向下移动其他项。

```
BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>parameters

*位置*<br/>
指定要在其之前插入新菜单项的菜单项。 可以通过以下方式使用*nFlags*参数解释*位置*：

|nFlags|位置的解释|
|------------|---------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 均未设置，则此值为默认值。|
|MF_BYPOSITION|指定参数提供现有菜单项的位置。 第一项的位置为0。 如果*位置*为-1，则新的菜单项将追加到菜单的末尾。|

*nFlags*<br/>
指定如何解释*位置*，并指定在将新菜单项添加到菜单时该菜单项的状态信息。 有关可以设置的标志的列表，请参阅[AppendMenu](#appendmenu)成员函数。 若要指定多个值，请使用按位 "或" 运算符将它们与 MF_BYCOMMAND 或 MF_BYPOSITION 标志进行组合。

*nIDNewItem*<br/>
指定新菜单项的命令 ID，或者，如果*nFlags*设置为 MF_POPUP，则为弹出菜单的菜单控点（HMENU）。 如果*nFlags*设置为 MF_SEPARATOR，则忽略*nIDNewItem*参数（不需要）。

*lpszNewItem*<br/>
指定新菜单项的内容。 *nFlags*可用于通过以下方式解释*lpszNewItem* ：

|nFlags|LpszNewItem 的解释|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含应用程序提供的32位值，应用程序可使用该值来维护与菜单项关联的附加数据。 此32位值可用于应用程序中由[WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem)和[WM_DRAWITEM](/windows/win32/Controls/wm-drawitem)消息提供的结构 `itemData` 成员中。 当菜单项最初显示或更改时，将发送这些消息。|
|MF_STRING|包含指向以 null 结尾的字符串的长指针。 这是默认的解释。|
|MF_SEPARATOR|忽略*lpszNewItem*参数（不需要）。|

*.Pbmp*<br/>
指向将用作菜单项的 `CBitmap` 对象。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

应用程序可以通过在*nFlags*中设置值来指定菜单项的状态。

每当窗口中的菜单发生更改（无论是否显示窗口）时，应用程序应调用 `CWnd::DrawMenuBar`。

当*nIDNewItem*指定一个弹出菜单时，它将成为插入它的菜单的一部分。 如果该菜单被销毁，则插入的菜单还将被销毁。 插入的菜单应该与 `CMenu` 对象分离，以避免冲突。

如果活动的多文档界面（MDI）子窗口已最大化，并且应用程序通过调用此函数并指定 MF_BYPOSITION 标志，将弹出菜单插入到 MDI 应用程序的菜单中，则会将该菜单插入一个远离结果. 出现这种情况的原因是活动 MDI 子窗口的 "控制" 菜单被插入到 MDI 框架窗口菜单栏的第一个位置。 若要正确地定位菜单，应用程序必须向要使用的位置值加1。 应用程序可以使用 WM_MDIGETACTIVE 消息来确定当前处于活动状态的子窗口是否处于最大化状态。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

##  <a name="insertmenuitem"></a>CMenu：： InsertMenuItem

在菜单中的指定位置插入新菜单项。

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>parameters

*uItem*<br/>
请参阅 Windows SDK 中[InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw)的*uItem*说明。

*lpMenuItemInfo*<br/>
请参阅 Windows SDK `InsertMenuItem` 中的*lpmii*说明。

*fByPos*<br/>
请参阅 Windows SDK `InsertMenuItem` 中的*fByPosition*说明。

### <a name="remarks"></a>备注

此函数包装 Windows SDK 中所述的[InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw)。

##  <a name="loadmenu"></a>CMenu：： LoadMenu

从应用程序的可执行文件加载菜单资源，并将其附加到 `CMenu` 对象上。

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>parameters

*lpszResourceName*<br/>
指向以 null 结尾的字符串，其中包含要加载的菜单资源的名称。

*nIDResource*<br/>
指定要加载的菜单资源的菜单 ID。

### <a name="return-value"></a>返回值

如果成功加载菜单资源，则为非零;否则为0。

### <a name="remarks"></a>备注

在退出之前，如果未将菜单分配给窗口，应用程序必须释放与菜单关联的系统资源。 应用程序通过调用[DestroyMenu](#destroymenu)成员函数来释放菜单。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

##  <a name="loadmenuindirect"></a>CMenu：： LoadMenuIndirect

从内存中的菜单模板加载资源，并将其附加到 `CMenu` 对象上。

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>parameters

*lpMenuTemplate*<br/>
指向菜单模板（单个[MENUITEMTEMPLATEHEADER](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader)结构和一个或多个[MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate)结构的集合）。 有关这两个结构的详细信息，请参阅 Windows SDK。

### <a name="return-value"></a>返回值

如果成功加载菜单资源，则为非零;否则为0。

### <a name="remarks"></a>备注

菜单模板是一个标头，后跟一个或多个[MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate)结构的集合，其中每个结构可能包含一个或多个菜单项和弹出菜单。

版本号应为0。

`mtOption` 标志应包括弹出列表中最后一项的 MF_END 和主列表中最后一项的。 请参阅 `AppendMenu` 成员函数了解其他标志。 当 MF_POPUP 在 `mtOption`中指定时，必须从 MENUITEMTEMPLATE 结构中省略 `mtId` 成员。

为 MENUITEMTEMPLATE 结构分配的空间必须足够大，以便 `mtString` 以 null 结尾的字符串的形式包含菜单项的名称。

在退出之前，如果未将菜单分配给窗口，应用程序必须释放与菜单关联的系统资源。 应用程序通过调用[DestroyMenu](#destroymenu)成员函数来释放菜单。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

##  <a name="m_hmenu"></a>CMenu：： m_hMenu

指定附加到 `CMenu` 对象的 Windows 菜单的 HMENU 句柄。

```
HMENU m_hMenu;
```

### <a name="example"></a>示例

  请参阅[CMenu：： LoadMenu](#loadmenu)的示例。

##  <a name="measureitem"></a>CMenu：： MeasureItem

当创建具有所有者描述样式的菜单时由框架调用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>parameters

*lpMeasureItemStruct*<br/>
指向 `MEASUREITEMSTRUCT` 结构的指针。

### <a name="remarks"></a>备注

默认情况下，此成员函数不执行任何操作。 重写此成员函数并填充 `MEASUREITEMSTRUCT` 结构以通知窗口菜单的尺寸。

有关 `MEASUREITEMSTRUCT` 结构的说明，请参阅[CWnd：： OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) 。

### <a name="example"></a>示例

以下代码来自 MFC [CTRLTEST](../../overview/visual-cpp-samples.md)示例：

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

##  <a name="modifymenu"></a>CMenu：： ModifyMenu

更改*位置*指定的位置处的现有菜单项。

```
BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>parameters

*位置*<br/>
指定要更改的菜单项。 可以通过以下方式使用*nFlags*参数解释*位置*：

|nFlags|位置的解释|
|------------|---------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 均未设置，则此值为默认值。|
|MF_BYPOSITION|指定参数提供现有菜单项的位置。 第一项的位置为0。|

*nFlags*<br/>
指定解释*位置*的方式，并提供有关要对菜单项进行的更改的信息。 有关可以设置的标志的列表，请参阅[AppendMenu](#appendmenu)成员函数。

*nIDNewItem*<br/>
指定修改的菜单项的命令 ID，或者，如果*nFlags*设置为 MF_POPUP，则为弹出菜单的菜单控点（HMENU）。 如果*nFlags*设置为 MF_SEPARATOR，则忽略*nIDNewItem*参数（不需要）。

*lpszNewItem*<br/>
指定新菜单项的内容。 可以通过以下方式使用*nFlags*参数解释*lpszNewItem* ：

|nFlags|LpszNewItem 的解释|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含应用程序提供的32位值，应用程序可使用该值来维护与菜单项关联的附加数据。 当应用程序处理 MF_MEASUREITEM 和 MF_DRAWITEM 时，此32位值可用于应用程序。|
|MF_STRING|包含指向以 null 结尾的字符串或 `CString`的长指针。|
|MF_SEPARATOR|忽略*lpszNewItem*参数（不需要）。|

*.Pbmp*<br/>
指向将用作菜单项的 `CBitmap` 对象。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

应用程序通过在*nFlags*中设置值来指定菜单项的新状态。 如果此函数替换与菜单项相关联的弹出菜单，它会销毁旧的弹出菜单并释放弹出菜单使用的内存。

当*nIDNewItem*指定一个弹出菜单时，它将成为插入它的菜单的一部分。 如果该菜单被销毁，则插入的菜单还将被销毁。 插入的菜单应该与 `CMenu` 对象分离，以避免冲突。

每当窗口中的菜单发生更改（无论是否显示窗口）时，应用程序应调用 `CWnd::DrawMenuBar`。 若要更改现有菜单项的特性，使用 `CheckMenuItem` 和 `EnableMenuItem` 成员函数的速度要快得多。

### <a name="example"></a>示例

  请参阅[CMenu：： InsertMenu](#insertmenu)的示例。

##  <a name="operator_hmenu"></a>CMenu：： operator HMENU

使用此运算符检索 `CMenu` 对象的句柄。

```
operator HMENU() const;
```

### <a name="return-value"></a>返回值

如果成功，则为 `CMenu` 对象的句柄;否则为 NULL。

### <a name="remarks"></a>备注

您可以使用句柄直接调用 Windows Api。

##  <a name="operator_neq"></a>CMenu：： operator！ =

确定两个菜单逻辑上是否不相等。

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>parameters

*下拉菜单*<br/>
一个用于比较的 `CMenu` 对象。

### <a name="remarks"></a>备注

测试左侧的菜单对象是否不等于右侧的菜单对象。

##  <a name="operator_eq_eq"></a>CMenu：： operator = =

确定两个菜单在逻辑上是否相等。

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>parameters

*下拉菜单*<br/>
一个用于比较的 `CMenu` 对象。

### <a name="remarks"></a>备注

测试左侧的 menu 对象是否等于（HMENU 值）到右侧的 menu 对象的位置。

##  <a name="removemenu"></a>CMenu：： RemoveMenu

从菜单中删除具有关联的弹出菜单的菜单项。

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>parameters

*位置*<br/>
指定要删除的菜单项。 可以通过以下方式使用*nFlags*参数解释*位置*：

|nFlags|位置的解释|
|------------|---------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 均未设置，则此值为默认值。|
|MF_BYPOSITION|指定参数提供现有菜单项的位置。 第一项的位置为0。|

*nFlags*<br/>
指定解释*位置*的方式。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

它不会销毁弹出菜单的句柄，因此可以重复使用菜单。 在调用此函数之前，应用程序可以调用 `GetSubMenu` 成员函数来检索弹出 `CMenu` 对象以供重复使用。

每当窗口中的菜单发生更改（无论是否显示窗口）时，应用程序必须调用 `CWnd::DrawMenuBar`。

### <a name="example"></a>示例

  请参阅[CMenu：： InsertMenu](#insertmenu)的示例。

##  <a name="setdefaultitem"></a>CMenu：： SetDefaultItem

设置指定菜单的默认菜单项。

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>parameters

*uItem*<br/>
新默认菜单项的标识符或位置，或为-1，表示没有默认项。 此参数的意义取决于*fByPos*的值。

*fByPos*<br/>
值，该值指定*uItem*的含义。 如果此参数为 FALSE，则*uItem*是一个菜单项标识符。 否则，它是菜单项的位置。

### <a name="return-value"></a>返回值

如果该函数成功，则返回值为非零值。 如果函数失败，则返回值为零。 若要获取更详细的错误信息，请使用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)，如 Windows SDK 中所述。

### <a name="remarks"></a>备注

此成员函数实现 Win32 函数[SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

  请参阅[CMenu：： InsertMenu](#insertmenu)的示例。

##  <a name="setmenucontexthelpid"></a>CMenu：： SetMenuContextHelpId

将上下文帮助 ID 与 `CMenu`相关联。

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>parameters

*dwContextHelpId*<br/>
要与 `CMenu`关联的上下文帮助 ID。

### <a name="return-value"></a>返回值

如果成功，则为非零值;否则为0

### <a name="remarks"></a>备注

菜单中的所有项都共享此标识符，不能将帮助上下文标识符附加到各个菜单项。

### <a name="example"></a>示例

  请参阅[CMenu：： InsertMenu](#insertmenu)的示例。

##  <a name="setmenuinfo"></a>CMenu：： SetMenuInfo

设置菜单的信息。

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>parameters

*lpcmi*<br/>
指向[MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo)结构的指针，该结构包含菜单的信息。

### <a name="return-value"></a>返回值

如果函数成功，则返回值为非零值;否则，返回值为零。

### <a name="remarks"></a>备注

调用此函数可设置有关菜单的特定信息。

##  <a name="setmenuitembitmaps"></a>CMenu：： SetMenuItemBitmaps

将指定的位图与菜单项相关联。

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>parameters

*位置*<br/>
指定要更改的菜单项。 可以通过以下方式使用*nFlags*参数解释*位置*：

|nFlags|位置的解释|
|------------|---------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果 MF_BYCOMMAND 和 MF_BYPOSITION 均未设置，则此值为默认值。|
|MF_BYPOSITION|指定参数提供现有菜单项的位置。 第一项的位置为0。|

*nFlags*<br/>
指定解释*位置*的方式。

*pBmpUnchecked*<br/>
指定要用于未选中的菜单项的位图。

*pBmpChecked*<br/>
指定要用于选定菜单项的位图。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

无论菜单项是选中还是未选中，Windows 都会在菜单项的旁边显示适当的位图。

如果*pBmpUnchecked*或*pBmpChecked*为 NULL，则 Windows 将不会在相应属性的菜单项旁显示任何内容。 如果两个参数均为 NULL，则在选中该项时，Windows 将使用默认复选标记，并在取消选中该项时删除复选标记。

如果菜单被销毁，则不会销毁这些位图;应用程序必须销毁它们。

Windows `GetMenuCheckMarkDimensions` 函数检索用于菜单项的默认复选标记的尺寸。 应用程序使用这些值来确定此函数提供的位图的适当大小。 获取大小，创建位图，然后对其进行设置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

##  <a name="setmenuiteminfo"></a>CMenu：： SetMenuItemInfo

更改有关菜单项的信息。

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>parameters

*uItem*<br/>
请参阅 Windows SDK 中[SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow)的*uItem*说明。

*lpMenuItemInfo*<br/>
请参阅 Windows SDK `SetMenuItemInfo` 中的*lpmii*说明。

*fByPos*<br/>
请参阅 Windows SDK `SetMenuItemInfo` 中的*fByPosition*说明。

### <a name="remarks"></a>备注

此函数包装 Windows SDK 中所述的[SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow)。

##  <a name="trackpopupmenu"></a>CMenu：： TrackPopupMenu

在指定位置显示一个浮动的弹出菜单，并在弹出菜单上跟踪项的选定内容。

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>parameters

*nFlags*<br/>
指定屏幕位置和鼠标位置标志。 有关可用标志的列表，请参阅[TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) 。

*x*<br/>
指定弹出菜单的屏幕坐标中的水平位置。 根据*nFlags*参数的值，菜单可以是左对齐、右对齐或相对于此位置居中。

*y*<br/>
指定屏幕上菜单顶部屏幕坐标中的垂直位置。

*pWnd*<br/>
标识拥有弹出菜单的窗口。 即使指定了 TPM_NONOTIFY 标志，此参数也不能为 NULL。 此窗口从菜单接收所有 WM_COMMAND 消息。 在 Windows 版本3.1 及更高版本中，在 `TrackPopupMenu` 返回之前，该窗口不会接收 WM_COMMAND 消息。 在 Windows 3.0 中，窗口在 `TrackPopupMenu` 返回之前接收 WM_COMMAND 消息。

*lpRect*<br/>
已忽略。

### <a name="return-value"></a>返回值

此方法返回 Windows SDK 中调用[TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)的结果。

### <a name="remarks"></a>备注

浮动的弹出菜单可出现在屏幕上的任何位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

##  <a name="trackpopupmenuex"></a>CMenu：： TrackPopupMenuEx

在指定位置显示一个浮动的弹出菜单，并在弹出菜单上跟踪项的选定内容。

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>parameters

*fuFlags*<br/>
为扩展菜单指定各种函数。 有关所有值及其含义的列表，请参阅[TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)。

*x*<br/>
指定弹出菜单的屏幕坐标中的水平位置。

*y*<br/>
指定屏幕上菜单顶部屏幕坐标中的垂直位置。

*pWnd*<br/>
指向包含弹出菜单并接收来自创建的菜单的消息的窗口的指针。 此窗口可以是来自当前应用程序的任何窗口，但不能为 NULL。 如果在*fuFlags*参数中指定 TPM_NONOTIFY，则该函数不会将任何消息发送到*pWnd*。 函数必须为*pWnd*指向的窗口返回，才能接收 WM_COMMAND 消息。

*lptpm*<br/>
指向[TPMPARAMS](/windows/win32/api/winuser/ns-winuser-tpmparams)结构的指针，该结构指定该菜单不应重叠的屏幕区域。 此参数可以为 NULL。

### <a name="return-value"></a>返回值

如果在*fuFlags*参数中指定 TPM_RETURNCMD，则返回值是用户选择的项的菜单项标识符。 如果用户在不进行选择的情况下取消菜单，或发生错误，则返回值为0。

如果未在*fuFlags*参数中指定 TPM_RETURNCMD，则如果函数成功，则返回值为非零; 否则返回值为0。 若要获取扩展的错误信息，请调用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>备注

浮动的弹出菜单可出现在屏幕上的任何位置。 若要详细了解如何在创建弹出菜单时处理错误，请参阅[TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)。

## <a name="see-also"></a>另请参阅

[MFC 示例 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)
