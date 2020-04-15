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
ms.openlocfilehash: 5ec97d8cf039034078f29b38fb6a41d6ff9a5e53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369983"
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
|[CMenu：CMenu](#cmenu)|构造 `CMenu` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|将新项目追加到此菜单的末尾。|
|[CMenu：：附加](#attach)|将 Windows 菜单句柄附加到`CMenu`对象。|
|[CMenu：：检查菜单项目](#checkmenuitem)|在弹出式菜单中，在菜单项旁边放置复选标记或删除复选标记。|
|[CMenu：：检查菜单广播项目](#checkmenuradioitem)|将单选按钮放在菜单项旁边，并从组中的所有其他菜单项中删除单选按钮。|
|[CMenu：：创建菜单](#createmenu)|创建一个空菜单并将其附加到`CMenu`对象。|
|[CMenu：：创建弹出菜单](#createpopupmenu)|创建一个空的弹出式菜单并将其附加到`CMenu`对象。|
|[CMenu：:DeleteMenu](#deletemenu)|从菜单中删除指定的项目。 如果菜单项具有关联的弹出式菜单，则销毁弹出窗口菜单的句柄并释放其使用的内存。|
|[CMenu：:D](#deletetempmap)|删除`FromHandle`成员函数创建`CMenu`的任何临时对象。|
|[CMenu：:D](#destroymenu)|销毁附加到`CMenu`对象的菜单，并释放菜单占用的任何内存。|
|[CMenu：:D埃塔奇](#detach)|从`CMenu`对象分离 Windows 菜单句柄并返回该句柄。|
|[CMenu：:D原始项目](#drawitem)|当所有者绘制的菜单的可视方面发生更改时，由框架调用。|
|[CMenu：启用菜单项目](#enablemenuitem)|启用、禁用或调暗（灰色）菜单项。|
|[CMenu：：从手柄](#fromhandle)|返回指向给定 Windows`CMenu`菜单句柄的对象的指针。|
|[CMenu：获取默认项目](#getdefaultitem)|确定指定菜单上的默认菜单项。|
|[CMenu：获取菜单上下文帮助 Id](#getmenucontexthelpid)|检索与菜单关联的帮助上下文 ID。|
|[CMenu：：获取菜单信息](#getmenuinfo)|检索特定菜单上的信息。|
|[CMenu：获取菜单项目计数](#getmenuitemcount)|确定弹出窗口或顶级菜单中的项目数。|
|[CMenu：获取菜单项目ID](#getmenuitemid)|获取位于指定位置的菜单项的菜单项标识符。|
|[CMenu：获取菜单项目信息](#getmenuiteminfo)|检索有关菜单项的信息。|
|[CMenu：：获取菜单](#getmenustate)|返回指定菜单项的状态或弹出式菜单中的项数。|
|[CMenu：：获取菜单字符串](#getmenustring)|检索指定菜单项的标签。|
|[CMenu：获取安全海菜单](#getsafehmenu)|返回此`m_hMenu``CMenu`对象包装。|
|[CMenu：获取子菜单](#getsubmenu)|检索指向弹出菜单的指针。|
|[CMenu::InsertMenu](#insertmenu)|在指定位置插入新菜单项，将其他项向下移动菜单。|
|[CMenu：插入菜单项目](#insertmenuitem)|在菜单中的指定位置插入新菜单项。|
|[CMenu：：加载菜单](#loadmenu)|从可执行文件中加载菜单资源并将其附加到`CMenu`对象。|
|[CMenu：：加载菜单间接](#loadmenuindirect)|从内存中的菜单模板加载菜单并将其附加到`CMenu`对象。|
|[CMenu：度量值项目](#measureitem)|由框架调用，以确定创建所有者绘制的菜单时的菜单维度。|
|[CMenu::ModifyMenu](#modifymenu)|在指定位置更改现有菜单项。|
|[CMenu：：删除菜单](#removemenu)|从指定的菜单中删除具有关联弹出式菜单的菜单项。|
|[CMenu：设置默认项目](#setdefaultitem)|设置指定菜单的默认菜单项。|
|[CMenu：设置菜单上下文帮助Id](#setmenucontexthelpid)|将帮助上下文 ID 设置为与菜单关联的帮助上下文 ID。|
|[CMenu：：设置菜单信息](#setmenuinfo)|设置特定菜单上的信息。|
|[CMenu：：设置菜单项目位图](#setmenuitembitmaps)|将指定的复选位图与菜单项关联。|
|[CMenu：：设置菜单项目信息](#setmenuiteminfo)|更改有关菜单项的信息。|
|[CMenu：：跟踪弹出菜单](#trackpopupmenu)|在指定位置显示浮动弹出式菜单，并跟踪弹出菜单上的项目选择。|
|[CMenu：：跟踪弹出菜单Ex](#trackpopupmenuex)|在指定位置显示浮动弹出式菜单，并跟踪弹出菜单上的项目选择。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CMenu：：操作员 HMENU](#operator_hmenu)|检索菜单对象的句柄。|
|[CMenu：：操作员！*](#operator_neq)|确定两个菜单对象是否相等。|
|[CMenu：：运算符 |](#operator_eq_eq)|确定两个菜单对象是否相等。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CMenu：：m_hMenu](#m_hmenu)|指定附加到对象的 Windows 菜单的`CMenu`句柄。|

## <a name="remarks"></a>备注

它提供了用于创建、跟踪、更新和销毁菜单的成员函数。

在堆`CMenu`栈帧上创建一个对象作为本地，然后`CMenu`调用 的成员函数根据需要操作新菜单。 接下来，调用[CWnd：：SetMenu](../../mfc/reference/cwnd-class.md#setmenu)将菜单设置为窗口，然后立即调用`CMenu`对象的["分离](#detach)"成员函数。 成员`CWnd::SetMenu`函数将窗口的菜单设置为新菜单，使窗口重新绘制以反映菜单更改，并将菜单的所有权传递给窗口。 调用`Detach`从`CMenu`对象分离 HMENU，以便在局部`CMenu`变量超过范围时，`CMenu`对象析构函数不会尝试销毁它不再拥有的菜单。 当窗口被破坏时，菜单本身会自动销毁。

您可以使用[LoadMenu 间接](#loadmenuindirect)成员函数从内存中的模板创建菜单，但更容易维护由调用[LoadMenu](#loadmenu)从资源创建的菜单，并且菜单资源管理器可以创建和修改菜单资源本身。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cmenuappendmenu"></a><a name="appendmenu"></a>CMenu：：附加菜单

将新项目追加到菜单的末尾。

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

### <a name="parameters"></a>参数

*nFlags*<br/>
指定新菜单项添加到菜单时的状态信息。 它由"备注"部分中列出的一个或多个值组成。

*nIDNewItem*<br/>
指定新菜单项的命令 ID，或者，如果*nFlags*设置为MF_POPUP，则指定弹出菜单的菜单`HMENU`句柄 （ ） 。 如果将 nFlags 设置为MF_SEPARATOR，则忽略 *（不需要）nIDNewItem*参数。 *nFlags*

*lpszNewItem*<br/>
指定新菜单项的内容。 *nFlags*参数用于以下列方式解释*lpszNewItem：*

|nFlags|lpszNewItem 的解释|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含应用程序提供的 32 位值，应用程序可以使用该值来维护与菜单项关联的其他数据。 当应用程序处理WM_MEASUREITEM和WM_DRAWITEM消息时，此 32 位值可供应用程序使用。 该值存储在这些消息提供`itemData`的结构成员中。|
|MF_STRING|包含指向 null 终止字符串的指针。 这是默认解释。|
|MF_SEPARATOR|*lpszNewItem 参数*将被忽略（不需要）。|

*pBmp*<br/>
指向将用作`CBitmap`菜单项的对象。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

应用程序可以通过在*nFlags*中设置值来指定菜单项的状态。 当*nIDNewItem*指定一个弹出式菜单时，它将成为附加该菜单的一部分。 如果该菜单被销毁，则附加的菜单也将销毁。 附加的菜单应与对象分离以避免`CMenu`冲突。 请注意，MF_STRING和MF_OWNERDRAW对 的`AppendMenu`位图版本无效。

以下列表描述可在*nFlags*中设置的标志 ：

- MF_CHECKED充当带有MF_UNCHECKED的切换，将默认复选标记放在项旁边。 当应用程序提供复选标记位图（请参阅[SetMenuItemBitmap](#setmenuitembitmaps)成员函数）时，将显示"复选标记"位图。

- MF_UNCHECKED充当带有MF_CHECKED的切换，以删除项目旁边的复选标记。 当应用程序提供复选标记位图（请参阅`SetMenuItemBitmaps`成员函数）时，将显示"复选标记关闭"位图。

- MF_DISABLED禁用菜单项，使其无法选择，但不会将其变暗。

- MF_ENABLED 启用菜单项，以便可以选择菜单项并将其从调光状态还原。

- MF_GRAYED禁用菜单项，使其无法选中并调暗。

- MF_MENUBARBREAK将项目放在静态菜单中的新行上，或在弹出式菜单中的新列中放置。 新的弹出式菜单列将与旧列分开，由垂直分隔线分隔。

- MF_MENUBREAK将项目放在静态菜单中的新行上，或在弹出式菜单中的新列中放置。 列之间没有放置分界线。

- MF_OWNERDRAW 指定该项目是所有者绘制项。 首次显示菜单时，拥有菜单的窗口将接收WM_MEASUREITEM消息，该消息检索菜单项的高度和宽度。 当所有者必须更新菜单项的可视外观时，WM_DRAWITEM消息是发送的消息。 此选项对顶级菜单项无效。

- MF_POPUP 指定菜单项具有与其关联的弹出式菜单。 ID 参数指定要与项关联的弹出式菜单的句柄。 这用于将顶级弹出式菜单或分层弹出式菜单添加到弹出式菜单项。

- MF_SEPARATOR绘制水平分界线。 只能在弹出式菜单中使用。 无法调暗、禁用或突出显示此行。 其他参数将被忽略。

- MF_STRING 指定菜单项是字符串。

以下每个组都列出互斥且不能一起使用的标志：

- MF_DISABLED、MF_ENABLED和MF_GRAYED

- MF_STRING、MF_OWNERDRAW、MF_SEPARATOR 和位图版本

- MF_MENUBARBREAK和MF_MENUBREAK

- MF_CHECKED和MF_UNCHECKED

每当位于窗口中的菜单发生更改（无论是否显示窗口），应用程序都应调用[CWnd：:DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)。

### <a name="example"></a>示例

  请参阅[CMenu：：createMenu](#createmenu)的示例。

## <a name="cmenuattach"></a><a name="attach"></a>CMenu：：附加

将现有的 Windows 菜单附加到`CMenu`对象。

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
指定 Windows 菜单的句柄。

### <a name="return-value"></a>返回值

如果操作成功，则非零;否则 0。

### <a name="remarks"></a>备注

如果菜单已附加到对象，`CMenu`则不应调用此功能。 菜单句柄存储在数据成员中`m_hMenu`。

如果要操作的菜单已与窗口关联，则可以使用[CWnd：：GetMenu](../../mfc/reference/cwnd-class.md#getmenu)函数获取菜单的句柄。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenucheckmenuitem"></a><a name="checkmenuitem"></a>CMenu：：检查菜单项目

向弹出式菜单中的菜单项添加复选标记或删除检查标记。

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>参数

*nID检查项目*<br/>
指定要检查的菜单项，由*nCheck*确定。

*n检查*<br/>
指定如何检查菜单项以及如何确定项目在菜单中的位置。 *nCheck*参数可以是具有MF_BYPOSITION或MF_BYCOMMAND标志的MF_CHECKED或MF_UNCHECKED的组合。 可以使用位或运算符组合这些标志。 它们具有以下含义：

- MF_BYCOMMAND 指定参数提供现有菜单项的命令 ID。 这是默认值。

- MF_BYPOSITION 指定参数给出现有菜单项的位置。 第一个项目位于位置 0。

- MF_CHECKED充当带有MF_UNCHECKED的切换，将默认复选标记放在项旁边。

- MF_UNCHECKED充当带有MF_CHECKED的切换，以删除项目旁边的复选标记。

### <a name="return-value"></a>返回值

项的上一个状态：MF_CHECKED或MF_UNCHECKED，或者如果菜单项不存在，则为 0xFFFFFFFFFF。

### <a name="remarks"></a>备注

*nIDCheckItem 参数*指定要修改的项。

*nIDCheckItem*参数可以标识弹出菜单项以及菜单项。 无需执行特殊步骤即可检查弹出式菜单项。 无法检查顶级菜单项。 必须按位置检查弹出式菜单项，因为它没有与其关联的菜单项标识符。

### <a name="example"></a>示例

  请参阅[CMenu：：GetMenustate 的示例](#getmenustate)。

## <a name="cmenucheckmenuradioitem"></a><a name="checkmenuradioitem"></a>CMenu：：检查菜单广播项目

检查指定的菜单项，使其成为一个单选项。

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>参数

*nID第一*<br/>
指定（作为 ID 或偏移，具体取决于*nFlags*的值）单选按钮组中的第一个菜单项。

*nIDLast*<br/>
指定（作为 ID 或偏移量，具体取决于*nFlags*的值）单选按钮组中的最后一个菜单项。

*nIDItem*<br/>
指定（作为 ID 或偏移，具体取决于*nFlags*的值），组中将用单选按钮检查的项。

*nFlags*<br/>
以下列方式指定*nIDFirst、nIDLast*和*nIDItem*的解释： *nIDLast*

|nFlags|解释|
|------------|--------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果未设置MF_BYCOMMAND或MF_BYPOSITION，则这是默认值。|
|MF_BYPOSITION|指定参数给出现有菜单项的位置。 第一个项目位于位置 0。|

### <a name="return-value"></a>返回值

如果成功，则非零;否则 0

### <a name="remarks"></a>备注

同时，函数将取消检查关联组中的所有其他菜单项，并清除这些项目的广播项类型标志。 选中的项目使用单选按钮（或项目符号）位图而不是复选标记位图显示。

### <a name="example"></a>示例

  请参阅[ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range)的示例。

## <a name="cmenucmenu"></a><a name="cmenu"></a>CMenu：CMenu

创建一个空菜单并将其附加到`CMenu`对象。

```
CMenu();
```

### <a name="remarks"></a>备注

在调用`CMenu:`

- [创建菜单](#createmenu)

- [创建弹出菜单](#createpopupmenu)

- [加载菜单](#loadmenu)

- [加载菜单间接](#loadmenuindirect)

- [Attach](#attach)

## <a name="cmenucreatemenu"></a><a name="createmenu"></a>CMenu：：创建菜单

创建菜单并将其附加到`CMenu`对象。

```
BOOL CreateMenu();
```

### <a name="return-value"></a>返回值

如果已成功创建菜单，则非零;否则 0。

### <a name="remarks"></a>备注

菜单最初为空。 可以使用`AppendMenu`或`InsertMenu`成员函数添加菜单项。

如果菜单分配给窗口，则当窗口被销毁时，它会自动销毁。

在退出之前，如果菜单未分配给窗口，则应用程序必须释放与菜单关联的系统资源。 应用程序通过调用[销毁菜单](#destroymenu)成员函数释放菜单。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

## <a name="cmenucreatepopupmenu"></a><a name="createpopupmenu"></a>CMenu：：创建弹出菜单

创建一个弹出式菜单并将其附加到`CMenu`对象。

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>返回值

成功创建弹出式菜单时非零;否则 0。

### <a name="remarks"></a>备注

菜单最初为空。 可以使用`AppendMenu`或`InsertMenu`成员函数添加菜单项。 应用程序可以将弹出式菜单添加到现有菜单或弹出式菜单。 成员`TrackPopupMenu`函数可用于将此菜单显示为浮动弹出式菜单，并跟踪弹出式菜单上的选择。

如果菜单分配给窗口，则当窗口被销毁时，它会自动销毁。 如果菜单添加到现有菜单中，则当该菜单被销毁时，该菜单将自动销毁。

在退出之前，如果菜单未分配给窗口，则应用程序必须释放与弹出式菜单关联的系统资源。 应用程序通过调用[销毁菜单](#destroymenu)成员函数释放菜单。

### <a name="example"></a>示例

  请参阅[CMenu：：createMenu](#createmenu)的示例。

## <a name="cmenudeletemenu"></a><a name="deletemenu"></a>CMenu：:DeleteMenu

从菜单中删除项目。

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>参数

*n位置*<br/>
指定要删除的菜单项，由*nFlags*确定。

*nFlags*<br/>
用于以下列方式解释*n定位*：

|nFlags|n定位的解释|
|------------|---------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果未设置MF_BYCOMMAND或MF_BYPOSITION，则这是默认值。|
|MF_BYPOSITION|指定参数给出现有菜单项的位置。 第一个项目位于位置 0。|

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

如果菜单项具有关联的弹出式菜单，则`DeleteMenu`销毁弹出窗口菜单的句柄并释放弹出菜单使用的内存。

每当位于窗口中的菜单发生更改（无论是否显示窗口），应用程序都必须调用[CWnd：:DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)。

### <a name="example"></a>示例

  请参阅[CWnd 的示例：：获取菜单](../../mfc/reference/cwnd-class.md#getmenu)。

## <a name="cmenudeletetempmap"></a><a name="deletetempmap"></a>CMenu：:D

由`CWinApp`空闲时间处理程序自动调用，删除[FromHandle](#fromhandle)成员`CMenu`函数创建的任何临时对象。

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>备注

`DeleteTempMap`在删除`CMenu``CMenu`对象之前，分离附加到临时对象的 Windows 菜单对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

## <a name="cmenudestroymenu"></a><a name="destroymenu"></a>CMenu：:D

销毁菜单和已使用的任何 Windows 资源。

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>返回值

如果菜单已销毁，则非零;否则 0。

### <a name="remarks"></a>备注

菜单在销毁之前与`CMenu`对象分离。 析`CMenu`构`DestroyMenu`函数中会自动调用 Windows 函数。

### <a name="example"></a>示例

  请参阅[CMenu：：createMenu](#createmenu)的示例。

## <a name="cmenudetach"></a><a name="detach"></a>CMenu：:D埃塔奇

从`CMenu`对象分离 Windows 菜单并返回句柄。

```
HMENU Detach();
```

### <a name="return-value"></a>返回值

HMENU 类型的句柄（如果成功）到 Windows 菜单;否则 NULL。

### <a name="remarks"></a>备注

数据`m_hMenu`成员设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenudrawitem"></a><a name="drawitem"></a>CMenu：:D原始项目

当所有者绘制的菜单的可视方面发生更改时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDraw 项目已结*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的指针，其中包含有关所需绘图类型的信息。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT`结构`itemAction`的成员定义要执行的绘图操作。 重写此成员函数以实现所有者绘制对象的绘图`CMenu`。 应用程序应还原在此成员函数终止之前为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 （GDI） 对象。

有关`DRAWITEMSTRUCT`结构的说明，请参阅[CWnd：OnDrawItem。](../../mfc/reference/cwnd-class.md#ondrawitem)

### <a name="example"></a>示例

以下代码来自 MFC [CTRLTEST](../../overview/visual-cpp-samples.md)示例：

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

## <a name="cmenuenablemenuitem"></a><a name="enablemenuitem"></a>CMenu：启用菜单项目

启用、禁用或调暗菜单项。

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>参数

*nID 启用项目*<br/>
指定要启用的菜单项，由*nEnable*确定。 此参数可以指定弹出式菜单项以及标准菜单项。

*n 启用*<br/>
指定要执行的操作。 它可以是MF_DISABLED、MF_ENABLED或MF_GRAYED的组合，具有MF_BYCOMMAND或MF_BYPOSITION。 可以使用位或运算符组合这些值。 这些值将具有以下含义：

- MF_BYCOMMAND 指定参数提供现有菜单项的命令 ID。 这是默认值。

- MF_BYPOSITION 指定参数给出现有菜单项的位置。 第一个项目位于位置 0。

- MF_DISABLED禁用菜单项，使其无法选择，但不会将其变暗。

- MF_ENABLED 启用菜单项，以便可以选择菜单项并将其从调光状态还原。

- MF_GRAYED禁用菜单项，使其无法选中并调暗。

### <a name="return-value"></a>返回值

以前的状态（MF_DISABLED、MF_ENABLED 或MF_GRAYED）或 -1（如果无效）。

### <a name="remarks"></a>备注

[CreateMenu、InsertMenu、](#createmenu)[修改菜单](#modifymenu)和[LoadMenu 间接](#loadmenuindirect)成员函数还可以设置菜单项的状态（已启用、禁用或调暗）。 [InsertMenu](#insertmenu)

使用MF_BYPOSITION值需要应用程序使用正确的`CMenu`。 如果使用菜单`CMenu`栏，则影响顶级菜单项（菜单栏中的项）。 要按位置设置弹出窗口或嵌套弹出式菜单中项目的状态，应用程序必须指定弹出式菜单的。 `CMenu`

当应用程序指定MF_BYCOMMAND标志时，Windows 会检查隶属于 的`CMenu`弹出菜单项。因此，除非存在重复的菜单项，`CMenu`否则使用菜单栏就足够了。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

## <a name="cmenufromhandle"></a><a name="fromhandle"></a>CMenu：：从手柄

将指向给定 Windows`CMenu`句柄的对象的指针返回到菜单。

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
菜单的 Windows 句柄。

### <a name="return-value"></a>返回值

指向`CMenu`的指针可能是临时的或永久性的。

### <a name="remarks"></a>备注

如果对象`CMenu`尚未附加到 Windows 菜单对象，则创建并附加临时`CMenu`对象。

此临时`CMenu`对象仅在下次应用程序在其事件循环中有空闲时间之前有效，此时将删除所有临时对象。

### <a name="example"></a>示例

  请参阅[CMenu：：createMenu](#createmenu)的示例。

## <a name="cmenugetdefaultitem"></a><a name="getdefaultitem"></a>CMenu：获取默认项目

确定指定菜单上的默认菜单项。

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>参数

*格迪旗*<br/>
指定函数如何搜索菜单项的值。 此参数可以是无、一个或以下值的组合：

|“值”|含义|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|指定，如果默认项是打开子菜单的项，则函数将在相应的子菜单中回放地搜索。 如果子菜单没有默认项，则返回值标识打开子菜单的项。<br /><br /> 默认情况下，该函数返回指定菜单上的第一个默认项，而不管它是否是打开子菜单的项。|
|GMDI_USEDISABLED|指定函数要返回默认项，即使它已禁用也是如此。<br /><br /> 默认情况下，该函数跳过禁用或灰显的项目。|

*fByPos*<br/>
指定是检索菜单项的标识符还是其位置的值。 如果此参数为 FALSE，则返回标识符。 否则，将返回该位置。

### <a name="return-value"></a>返回值

如果函数成功，则返回值是菜单项的标识符或位置。 如果函数失败，返回值为 - 1。

### <a name="remarks"></a>备注

此成员函数实现 Win32 函数[GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

  请参阅[CMenu：：插入菜单](#insertmenu)的示例。

## <a name="cmenugetmenucontexthelpid"></a><a name="getmenucontexthelpid"></a>CMenu：获取菜单上下文帮助 Id

检索与`CMenu`关联的上下文帮助 ID。

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>返回值

上下文帮助 ID 当前与其`CMenu`关联（如果有）零否则。

### <a name="example"></a>示例

  请参阅[CMenu：：插入菜单](#insertmenu)的示例。

## <a name="cmenugetmenuinfo"></a><a name="getmenuinfo"></a>CMenu：：获取菜单信息

检索菜单的信息。

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>参数

*lpcmi*<br/>
指向[MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo)结构的指针，其中包含菜单的信息。

### <a name="return-value"></a>返回值

如果函数成功，则返回值为非零;否则，返回值为零。

### <a name="remarks"></a>备注

调用此函数以检索有关菜单的信息。

## <a name="cmenugetmenuitemcount"></a><a name="getmenuitemcount"></a>CMenu：获取菜单项目计数

确定弹出窗口或顶级菜单中的项目数。

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>返回值

如果函数成功，则菜单中的项数;否则 -1。

### <a name="example"></a>示例

  请参阅[CWnd 的示例：：获取菜单](../../mfc/reference/cwnd-class.md#getmenu)。

## <a name="cmenugetmenuitemid"></a><a name="getmenuitemid"></a>CMenu：获取菜单项目ID

获取位于*nPos*定义位置的菜单项的菜单项标识符。

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定正在检索其 ID 的菜单项的位置（从零开始）。

### <a name="return-value"></a>返回值

如果函数成功，则弹出菜单中指定项的项目 ID。 如果指定的项是弹出式菜单（与弹出菜单中的项相反），则返回值为 -1。 如果*nPos*对应于 SEPARATOR 菜单项，则返回值为 0。

### <a name="example"></a>示例

  请参阅[CMenu：：插入菜单](#insertmenu)的示例。

## <a name="cmenugetmenuiteminfo"></a><a name="getmenuiteminfo"></a>CMenu：获取菜单项目信息

检索有关菜单项的信息。

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>参数

*uItem*<br/>
要获取有关获取信息的菜单项的标识符或位置。 此参数的含义取决于 的值`ByPos`。

*lpMenu项目信息*<br/>
指向[MenuITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow)的指针，如 Windows SDK 中所述，其中包含有关菜单的信息。

*fByPos*<br/>
指定`nIDItem`的含义的值。 默认情况下，FALSE`ByPos`表示 uItem 是菜单项标识符。 如果未`ByPos`设置为 FALSE，则指示菜单项位置。

### <a name="return-value"></a>返回值

如果函数成功，则返回值为非零。 如果函数失败，则返回值为零。 要获取扩展的错误信息，请使用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)，如 Windows SDK 中所述。

### <a name="remarks"></a>备注

此成员函数实现 Win32 函数[GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow)的行为，如 Windows SDK 中所述。 请注意，在 MFC 实现`GetMenuItemInfo`中，您不使用对菜单的句柄。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

## <a name="cmenugetmenustate"></a><a name="getmenustate"></a>CMenu：：获取菜单

返回指定菜单项的状态或弹出式菜单中的项数。

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>参数

*nID*<br/>
指定菜单项 ID，由*nFlags*确定。

*nFlags*<br/>
指定*nID*的性质 。 可以为下列值之一：

- MF_BYCOMMAND 指定参数提供现有菜单项的命令 ID。 这是默认值。

- MF_BYPOSITION 指定参数给出现有菜单项的位置。 第一个项目位于位置 0。

### <a name="return-value"></a>返回值

如果指定的项不存在，则值 0xFFFFFFFFFFFFFF。 如果*nId*标识了弹出式菜单，则高阶字节包含弹出式菜单中的项数，低阶字节包含与弹出式菜单关联的菜单标志。 否则，返回值是以下列表中值的掩码 （Boolean OR）（此掩码描述*nId*标识的菜单项的状态）：

- MF_CHECKED充当带有MF_UNCHECKED的切换，将默认复选标记放在项旁边。 当应用程序提供复选标记位图（请参阅`SetMenuItemBitmaps`成员函数）时，将显示"复选标记"位图。

- MF_DISABLED禁用菜单项，使其无法选择，但不会将其变暗。

- MF_ENABLED 启用菜单项，以便可以选择菜单项并将其从调光状态还原。 请注意，此常量的值为 0;因此，此常量的值为 0。使用此值时，应用程序不应针对 0 测试失败。

- MF_GRAYED禁用菜单项，使其无法选中并调暗。

- MF_MENUBARBREAK将项目放在静态菜单中的新行上，或在弹出式菜单中的新列中放置。 新的弹出式菜单列将与旧列分开，由垂直分隔线分隔。

- MF_MENUBREAK将项目放在静态菜单中的新行上，或在弹出式菜单中的新列中放置。 列之间没有放置分界线。

- MF_SEPARATOR绘制水平分界线。 只能在弹出式菜单中使用。 无法调暗、禁用或突出显示此行。 其他参数将被忽略。

- MF_UNCHECKED充当带有MF_CHECKED的切换，以删除项目旁边的复选标记。 当应用程序提供复选标记位图（请参阅`SetMenuItemBitmaps`成员函数）时，将显示"复选标记关闭"位图。 请注意，此常量的值为 0;因此，此常量的值为 0。使用此值时，应用程序不应针对 0 测试失败。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

## <a name="cmenugetmenustring"></a><a name="getmenustring"></a>CMenu：：获取菜单字符串

将指定菜单项的标签复制到指定的缓冲区。

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

### <a name="parameters"></a>参数

*nIDItem*<br/>
指定菜单项的整数标识符或菜单中的菜单项的偏移量，具体取决于*nFlags*的值。

*lpString*<br/>
指向要接收标签的缓冲区。

*rString*<br/>
对要接收复制`CString`的菜单字符串的对象的引用。

*nMaxCount*<br/>
指定要复制的标签的最大长度（以字符表示）。 如果标签长于*nMaxCount*中指定的最大值，则额外的字符将被截断。

*nFlags*<br/>
指定*nIDItem*参数的解释。 可以为下列值之一：

|nFlags|nIDItem 的解释|
|------------|-------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果未设置MF_BYCOMMAND或MF_BYPOSITION，则这是默认值。|
|MF_BYPOSITION|指定参数给出现有菜单项的位置。 第一个项目位于位置 0。|

### <a name="return-value"></a>返回值

指定复制到缓冲区的实际字符数，不包括空终止符。

### <a name="remarks"></a>备注

*nMaxCount*参数应大于标签中的字符数，以适应终止字符串的空字符。

### <a name="example"></a>示例

  请参阅[CMenu：：插入菜单](#insertmenu)的示例。

## <a name="cmenugetsafehmenu"></a><a name="getsafehmenu"></a>CMenu：获取安全海菜单

返回由此`CMenu`对象包裹的 HMENU 或`CMenu`NULL 指针。

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>示例

  请参阅[CMenu：：LoadMenu](#loadmenu)的示例。

## <a name="cmenugetsubmenu"></a><a name="getsubmenu"></a>CMenu：获取子菜单

检索弹出式菜单`CMenu`的对象。

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定菜单中包含的弹出式菜单的位置。 对于第一个菜单项，位置值从 0 开始。 在此函数中不能使用弹出式菜单的标识符。

### <a name="return-value"></a>返回值

指向对象（`CMenu`如果给定位置`m_hMenu`存在弹出菜单）时，其成员包含对弹出菜单的句柄的指针;否则 NULL。 如果`CMenu`对象不存在，则创建临时对象。 不应`CMenu`存储返回的指针。

### <a name="example"></a>示例

  请参阅[CMenu 示例：：TrackPopupMenu](#trackpopupmenu)。

## <a name="cmenuinsertmenu"></a><a name="insertmenu"></a>CMenu：插入菜单

在*n定位*指定的位置插入新菜单项，并将其他项移下菜单。

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

### <a name="parameters"></a>参数

*n位置*<br/>
指定要插入新菜单项之前的菜单项。 *nFlags*参数可用于以以下方式解释*n定位*：

|nFlags|n定位的解释|
|------------|---------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果未设置MF_BYCOMMAND或MF_BYPOSITION，则这是默认值。|
|MF_BYPOSITION|指定参数给出现有菜单项的位置。 第一个项目位于位置 0。 如果*n定位*为 -1，则新菜单项将追加到菜单的末尾。|

*nFlags*<br/>
指定如何解释*n定位，* 并指定新菜单项添加到菜单时的状态信息。 有关可能设置的标志的列表，请参阅[AppendMenu](#appendmenu)成员函数。 要指定多个值，请使用位或运算符将它们与MF_BYCOMMAND或MF_BYPOSITION标志组合。

*nIDNewItem*<br/>
指定新菜单项的命令 ID，或者，如果*nFlags*设置为MF_POPUP，则指定弹出菜单的菜单句柄 （HMENU）。 如果将 nFlags 设置为MF_SEPARATOR，则忽略 *（不需要）nIDNewItem*参数。 *nFlags*

*lpszNewItem*<br/>
指定新菜单项的内容。 *nFlags*可用于以以下方式解释*lpszNewItem：*

|nFlags|lpszNewItem 的解释|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含应用程序提供的 32 位值，应用程序可以使用该值来维护与菜单项关联的其他数据。 此 32 位值可用于[WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem)和[WM_DRAWITEM](/windows/win32/Controls/wm-drawitem)消息提供`itemData`的结构成员中的应用程序。 这些消息在最初显示或更改菜单项时发送。|
|MF_STRING|包含指向 null 终止字符串的长指针。 这是默认解释。|
|MF_SEPARATOR|*lpszNewItem 参数*将被忽略（不需要）。|

*pBmp*<br/>
指向将用作`CBitmap`菜单项的对象。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

应用程序可以通过在*nFlags*中设置值来指定菜单项的状态。

每当位于窗口中的菜单发生更改（无论是否显示窗口），应用程序都应调用`CWnd::DrawMenuBar`。

当*nIDNewItem*指定一个弹出式菜单时，它将成为插入该菜单的菜单的一部分。 如果该菜单已销毁，则插入的菜单也将销毁。 插入的菜单应从`CMenu`对象分离以避免冲突。

如果活动多个文档接口 （MDI） 子窗口最大化，并且应用程序通过调用此函数并指定MF_BYPOSITION标志将弹出菜单插入到 MDI 应用程序的菜单中，则菜单将插入比预期更远的位置。 这是因为活动 MDI 子窗口的控制菜单插入到 MDI 框架窗口菜单栏的第一个位置。 要正确放置菜单，应用程序必须向其他使用的位置值添加 1。 应用程序可以使用WM_MDIGETACTIVE消息来确定当前活动的子窗口是否最大化。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

## <a name="cmenuinsertmenuitem"></a><a name="insertmenuitem"></a>CMenu：插入菜单项目

在菜单中的指定位置插入新菜单项。

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>参数

*uItem*<br/>
请参阅 Windows SDK 中的[插入菜单项](/windows/win32/api/winuser/nf-winuser-insertmenuitemw)中的*u 项目*说明。

*lpMenu项目信息*<br/>
请参阅 Windows SDK 中`InsertMenuItem` *lpmii*的说明。

*fByPos*<br/>
请参阅 Windows SDK 中的`InsertMenuItem` *fBy定位*说明。

### <a name="remarks"></a>备注

此函数包装[InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw)，在 Windows SDK 中描述。

## <a name="cmenuloadmenu"></a><a name="loadmenu"></a>CMenu：：加载菜单

从应用程序的可执行文件加载菜单资源并将其附加到`CMenu`对象。

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>参数

*lpsz 资源名称*<br/>
指向包含要加载的菜单资源名称的 null 端接字符串。

*nID资源*<br/>
指定要加载的菜单资源的菜单 ID。

### <a name="return-value"></a>返回值

如果菜单资源已成功加载，则非零;否则 0。

### <a name="remarks"></a>备注

在退出之前，如果菜单未分配给窗口，则应用程序必须释放与菜单关联的系统资源。 应用程序通过调用[销毁菜单](#destroymenu)成员函数释放菜单。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

## <a name="cmenuloadmenuindirect"></a><a name="loadmenuindirect"></a>CMenu：：加载菜单间接

从内存中的菜单模板加载资源并将其附加到`CMenu`对象。

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>参数

*lpMenu模板*<br/>
指向菜单模板（这是单个[菜单项目模板](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader)结构以及一个或多个[MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate)结构的集合）。 有关这两个结构的详细信息，请参阅 Windows SDK。

### <a name="return-value"></a>返回值

如果菜单资源已成功加载，则非零;否则 0。

### <a name="remarks"></a>备注

菜单模板是一个标头，后跟一个或多个[MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate)结构的集合，每个结构可能包含一个或多个菜单项和弹出菜单。

版本号应为 0。

标志`mtOption`应包括弹出列表中最后一个项目和主列表中的最后一项MF_END。 有关其他`AppendMenu`标志，请参阅成员函数。 在`mtId`中`mtOption`指定MF_POPUP时，必须从 MENUITEMTEMPLATE 结构中省略该成员。

为 MENUITEMTEMPLATE 结构分配的空间必须足够大，以便`mtString`将菜单项的名称作为 null 终止字符串。

在退出之前，如果菜单未分配给窗口，则应用程序必须释放与菜单关联的系统资源。 应用程序通过调用[销毁菜单](#destroymenu)成员函数释放菜单。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

## <a name="cmenum_hmenu"></a><a name="m_hmenu"></a>CMenu：：m_hMenu

指定附加到对象的 Windows 菜单的`CMenu`HMENU 句柄。

```
HMENU m_hMenu;
```

### <a name="example"></a>示例

  请参阅[CMenu：：LoadMenu](#loadmenu)的示例。

## <a name="cmenumeasureitem"></a><a name="measureitem"></a>CMenu：度量值项目

创建具有所有者绘制样式的菜单时，由框架调用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>参数

*lp 测量项目结构*<br/>
指向结构的`MEASUREITEMSTRUCT`指针。

### <a name="remarks"></a>备注

默认情况下，此成员函数不执行任何操作。 覆盖此成员函数并填充`MEASUREITEMSTRUCT`结构以通知 Windows 菜单的尺寸。

有关`MEASUREITEMSTRUCT`结构的说明，请参阅[CWnd：onMeasureItem。](../../mfc/reference/cwnd-class.md#onmeasureitem)

### <a name="example"></a>示例

以下代码来自 MFC [CTRLTEST](../../overview/visual-cpp-samples.md)示例：

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

## <a name="cmenumodifymenu"></a><a name="modifymenu"></a>CMenu：：修改菜单

在*n定位*指定的位置更改现有菜单项。

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

### <a name="parameters"></a>参数

*n位置*<br/>
指定要更改的菜单项。 *nFlags*参数可用于以以下方式解释*n定位*：

|nFlags|n定位的解释|
|------------|---------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果未设置MF_BYCOMMAND或MF_BYPOSITION，则这是默认值。|
|MF_BYPOSITION|指定参数给出现有菜单项的位置。 第一个项目位于位置 0。|

*nFlags*<br/>
指定如何解释*n定位*，并提供有关要对菜单项所做的更改的信息。 有关可能设置的标志列表，请参阅[AppendMenu](#appendmenu)成员函数。

*nIDNewItem*<br/>
指定修改菜单项的命令 ID，或者，如果*nFlags*设置为MF_POPUP，则指定弹出式菜单的菜单句柄 （HMENU）。 如果将 nFlags 设置为MF_SEPARATOR，则忽略 *（不需要）nIDNewItem*参数。 *nFlags*

*lpszNewItem*<br/>
指定新菜单项的内容。 *nFlags*参数可用于以以下方式解释*lpszNewItem：*

|nFlags|lpszNewItem 的解释|
|------------|-----------------------------------|
|MF_OWNERDRAW|包含应用程序提供的 32 位值，应用程序可以使用该值来维护与菜单项关联的其他数据。 当应用程序处理MF_MEASUREITEM和MF_DRAWITEM时，此 32 位值可供应用程序使用。|
|MF_STRING|包含指向 null 终止字符串或 的长`CString`指针。|
|MF_SEPARATOR|*lpszNewItem 参数*将被忽略（不需要）。|

*pBmp*<br/>
指向将用作`CBitmap`菜单项的对象。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

应用程序通过在*nFlags*中设置值来指定菜单项的新状态。 如果此函数替换与菜单项关联的弹出式菜单，它将销毁旧的弹出式菜单并释放弹出式菜单使用的内存。

当*nIDNewItem*指定一个弹出式菜单时，它将成为插入该菜单的菜单的一部分。 如果该菜单已销毁，则插入的菜单也将销毁。 插入的菜单应从`CMenu`对象分离以避免冲突。

每当位于窗口中的菜单发生更改（无论是否显示窗口），应用程序都应调用`CWnd::DrawMenuBar`。 要更改现有菜单项的属性，使用`CheckMenuItem`和`EnableMenuItem`成员函数要快得多。

### <a name="example"></a>示例

  请参阅[CMenu：：插入菜单](#insertmenu)的示例。

## <a name="cmenuoperator-hmenu"></a><a name="operator_hmenu"></a>CMenu：：操作员 HMENU

使用此运算符检索`CMenu`对象的句柄。

```
operator HMENU() const;
```

### <a name="return-value"></a>返回值

如果成功，则处理`CMenu`对象的句柄;否则，NULL。

### <a name="remarks"></a>备注

您可以使用该句柄直接调用 Windows API。

## <a name="cmenuoperator-"></a><a name="operator_neq"></a>CMenu：：操作员！*

确定两个菜单在逻辑上是否相等。

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>参数

*菜单*<br/>
一个用于比较的 `CMenu` 对象。

### <a name="remarks"></a>备注

测试左侧的菜单对象是否不等于右侧的菜单对象。

## <a name="cmenuoperator-"></a><a name="operator_eq_eq"></a>CMenu：：运算符 |

确定两个菜单在逻辑上是否相等。

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>参数

*菜单*<br/>
一个用于比较的 `CMenu` 对象。

### <a name="remarks"></a>备注

测试左侧的菜单对象与右侧的菜单对象是否相等（就 HMENU 值而言）。

## <a name="cmenuremovemenu"></a><a name="removemenu"></a>CMenu：：删除菜单

从菜单中删除具有关联弹出式菜单的菜单项。

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>参数

*n位置*<br/>
指定要删除的菜单项。 *nFlags*参数可用于以以下方式解释*n定位*：

|nFlags|n定位的解释|
|------------|---------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果未设置MF_BYCOMMAND或MF_BYPOSITION，则这是默认值。|
|MF_BYPOSITION|指定参数给出现有菜单项的位置。 第一个项目位于位置 0。|

*nFlags*<br/>
指定如何解释*n定位*。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

它不会破坏弹出式菜单的句柄，因此菜单可以重复使用。 在调用此函数之前，应用程序可以调用`GetSubMenu`成员函数来检索弹出`CMenu`对象以供重用。

每当位于窗口中的菜单发生更改（无论是否显示窗口），应用程序都必须调用`CWnd::DrawMenuBar`。

### <a name="example"></a>示例

  请参阅[CMenu：：插入菜单](#insertmenu)的示例。

## <a name="cmenusetdefaultitem"></a><a name="setdefaultitem"></a>CMenu：设置默认项目

设置指定菜单的默认菜单项。

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>参数

*uItem*<br/>
新默认菜单项的标识符或位置， 或 - 1，表示没有默认项。 此参数的含义取决于*fByPos*的值。

*fByPos*<br/>
指定*uItem*的含义的值。 如果此参数为 FALSE，*则 uItem*是菜单项标识符。 否则，它是菜单项位置。

### <a name="return-value"></a>返回值

如果函数成功，则返回值为非零。 如果函数失败，则返回值为零。 要获取扩展的错误信息，请使用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)，如 Windows SDK 中所述。

### <a name="remarks"></a>备注

此成员函数实现 Win32 函数[SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

  请参阅[CMenu：：插入菜单](#insertmenu)的示例。

## <a name="cmenusetmenucontexthelpid"></a><a name="setmenucontexthelpid"></a>CMenu：设置菜单上下文帮助Id

将上下文帮助 ID`CMenu`与 关联。

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>参数

*dwContextHelpId*<br/>
要与`CMenu`关联的上下文帮助 ID。

### <a name="return-value"></a>返回值

如果成功，则非零;否则 0

### <a name="remarks"></a>备注

菜单中的所有项都共享此标识符 - 无法将帮助上下文标识符附加到各个菜单项。

### <a name="example"></a>示例

  请参阅[CMenu：：插入菜单](#insertmenu)的示例。

## <a name="cmenusetmenuinfo"></a><a name="setmenuinfo"></a>CMenu：：设置菜单信息

设置菜单的信息。

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>参数

*lpcmi*<br/>
指向[MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo)结构的指针，其中包含菜单的信息。

### <a name="return-value"></a>返回值

如果函数成功，则返回值为非零;否则，返回值为零。

### <a name="remarks"></a>备注

调用此函数以设置有关菜单的特定信息。

## <a name="cmenusetmenuitembitmaps"></a><a name="setmenuitembitmaps"></a>CMenu：：设置菜单项目位图

将指定的位图与菜单项关联。

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>参数

*n位置*<br/>
指定要更改的菜单项。 *nFlags*参数可用于以以下方式解释*n定位*：

|nFlags|n定位的解释|
|------------|---------------------------------|
|MF_BYCOMMAND|指定参数提供现有菜单项的命令 ID。 如果未设置MF_BYCOMMAND或MF_BYPOSITION，则这是默认值。|
|MF_BYPOSITION|指定参数给出现有菜单项的位置。 第一个项目位于位置 0。|

*nFlags*<br/>
指定如何解释*n定位*。

*pBmp 未选中*<br/>
指定未选中的菜单项要使用的位图。

*pBmpChecked*<br/>
指定要用于选中的菜单项的位图。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

无论菜单项是选中还是未选中，Windows 都会在菜单项旁边显示相应的位图。

如果*pBmpUnchecked*或*pBmpChecked*为 NULL，则 Windows 在相应属性的菜单项旁边不显示任何内容。 如果两个参数都是 NULL，则 Windows 在检查项目时使用默认复选标记，并在取消选中项目时删除复选标记。

当菜单被销毁时，这些位图不会被销毁;但是，这些位图不会被销毁。应用程序必须销毁它们。

Windows`GetMenuCheckMarkDimensions`函数检索用于菜单项的默认复选标记的尺寸。 应用程序使用这些值来确定此函数提供的位图的适当大小。 获取大小，创建位图，然后设置它们。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

## <a name="cmenusetmenuiteminfo"></a><a name="setmenuiteminfo"></a>CMenu：：设置菜单项目信息

更改有关菜单项的信息。

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>参数

*uItem*<br/>
请参阅 Windows SDK 中的["SetMenuItemInfo"](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow)中的*u 项目*说明。

*lpMenu项目信息*<br/>
请参阅 Windows SDK 中`SetMenuItemInfo` *lpmii*的说明。

*fByPos*<br/>
请参阅 Windows SDK 中的`SetMenuItemInfo` *fBy定位*说明。

### <a name="remarks"></a>备注

此函数包装在 Windows SDK 中描述的[SetMenuItemInfo。](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow)

## <a name="cmenutrackpopupmenu"></a><a name="trackpopupmenu"></a>CMenu：：跟踪弹出菜单

在指定位置显示浮动弹出式菜单，并跟踪弹出菜单上的项目选择。

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>参数

*nFlags*<br/>
指定屏幕位置和鼠标位置标志。 有关可用标志的列表，请参阅[TrackPopupMenu。](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)

** x <br/>
指定弹出式菜单的屏幕坐标中的水平位置。 根据*nFlags*参数的值，菜单可以左对齐、右对齐或相对于此位置居中。

*Y*<br/>
指定屏幕坐标中屏幕坐标中的垂直位置。

*pwnd*<br/>
标识拥有弹出式菜单的窗口。 即使指定了TPM_NONOTIFY标志，此参数也不能为 NULL。 此窗口从菜单接收所有WM_COMMAND消息。 在 Windows 版本 3.1 和更高版本中，窗口在返回`TrackPopupMenu`之前不会接收WM_COMMAND消息。 在 Windows 3.0 中，窗口在返回`TrackPopupMenu`之前接收WM_COMMAND消息。

*lpRect*<br/>
已忽略。

### <a name="return-value"></a>返回值

此方法返回在 Windows SDK 中调用[TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)的结果。

### <a name="remarks"></a>备注

浮动弹出式菜单可以出现在屏幕上的任意位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

## <a name="cmenutrackpopupmenuex"></a><a name="trackpopupmenuex"></a>CMenu：：跟踪弹出菜单Ex

在指定位置显示浮动弹出式菜单，并跟踪弹出菜单上的项目选择。

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>参数

*福旗*<br/>
为扩展菜单指定各种功能。 有关所有值及其含义的列表，请参阅[TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)。

** x <br/>
指定弹出式菜单的屏幕坐标中的水平位置。

*Y*<br/>
指定屏幕坐标中屏幕坐标中的垂直位置。

*pwnd*<br/>
指向具有弹出菜单并从创建的菜单接收消息的窗口的指针。 此窗口可以是当前应用程序的任何窗口，但不能为 NULL。 如果在*fuFlags*参数中指定TPM_NONOTIFY，则函数不会向*pWnd*发送任何消息。 函数必须返回*pWnd*指向的窗口才能接收WM_COMMAND消息。

*lptpm*<br/>
指向[TPMPARAMS](/windows/win32/api/winuser/ns-winuser-tpmparams)结构的指针，该结构指定菜单不应重叠的屏幕区域。 此参数可以是 NULL。

### <a name="return-value"></a>返回值

如果在*fuFlags*参数中指定TPM_RETURNCMD，则返回值是用户选择的项的菜单项标识符。 如果用户取消菜单而不进行选择，或者如果发生错误，则返回值为 0。

如果未在*fuFlags*参数中指定TPM_RETURNCMD，则如果函数成功，返回值为非零;如果函数失败，则返回值为 0。 要获取扩展的错误信息，请致电[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>备注

浮动弹出式菜单可以出现在屏幕上的任意位置。 有关创建弹出式菜单时处理错误的详细信息，请参阅[TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex)。

## <a name="see-also"></a>另请参阅

[MFC 样品 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)
