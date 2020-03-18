---
title: 消息映射宏 (MFC)
ms.date: 03/27/2019
f1_keywords:
- AFXWIN/DECLARE_MESSAGE_MAP
- AFXWIN/BEGIN_MESSAGE_MAP
- AFXWIN/BEGIN_TEMPLATE_MESSAGE_MAP
- AFXWIN/END_MESSAGE_MAP
- AFXWIN/ON_COMMAND
- AFXWIN/ON_COMMAND_EX
- AFXWIN/ON_CONTROL
- AFXWIN/ON_MESSAGE
- AFXWIN/ON_OLECMD
- AFXWIN/ON_REGISTERED_MESSAGE
- AFXWIN/ON_REGISTERED_THREAD_MESSAGE
- AFXWIN/ON_THREAD_MESSAGE
- AFXWIN/ON_UPDATE_COMMAND_UI
- AFXWIN/ON_COMMAND_RANGE
- AFXWIN/ON_UPDATE_COMMAND_UI_RANGE
- AFXWIN/ON_CONTROL_RANGE
helpviewer_keywords:
- message map macros
- Windows messages [MFC], declaration
- demarcating Windows messages
- message maps [MFC], macros
- message maps [MFC], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
ms.openlocfilehash: b88b745e3b70cf030f77f247ab03cd69d910109f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426347"
---
# <a name="message-map-macros-mfc"></a>消息映射宏 (MFC)

为了支持消息映射，MFC 提供了以下宏：

### <a name="message-map-declaration-and-demarcation-macros"></a>消息映射声明和分界宏

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|声明将在类中使用消息映射来将消息映射到函数（必须在类声明中使用）。|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|开始消息映射的定义（必须在类实现中使用）。|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|开始对包含单个模板参数的类类型的消息映射的定义。 |
|[END_MESSAGE_MAP](#end_message_map)|结束消息映射的定义（必须在类实现中使用）。|

### <a name="message-mapping-macros"></a>消息映射宏

|||
|-|-|
|[ON_COMMAND](#on_command)|指示哪个函数将处理指定的命令消息。|
|[ON_COMMAND_EX](#on_command_ex)|指示哪个函数将处理指定的命令消息。|
|[ON_CONTROL](#on_control)|指示哪个函数将处理指定的控件通知消息。|
|[ON_MESSAGE](#on_message)|指示哪个函数将处理用户定义的消息。|
|[ON_OLECMD](#on_olecmd)|指示哪个函数将处理 DocObject 或其容器中的菜单命令。|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|指示哪个函数将处理已注册的用户定义消息。|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|指示哪个函数将在您具有 `CWinThread` 类时处理已注册的用户定义消息。|
|[ON_THREAD_MESSAGE](#on_thread_message)|指示哪个函数将在您具有 `CWinThread` 类时处理用户定义的消息。|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|指示哪个函数将处理指定的用户界面更新命令消息。|

### <a name="message-map-range-macros"></a>消息映射范围宏

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|指示哪个函数将处理在宏的前两个参数中指定的命令 ID 的范围。|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|指示哪个更新处理程序将处理在宏的前两个参数中指定的命令 ID 的范围。|
|[ON_CONTROL_RANGE](#on_control_range)|指示哪个函数将处理来自在宏的第二个和第三个参数中指定的控件 ID 的范围的通知。 第一个参数是控件通知消息，如 BN_CLICKED。|

有关消息映射、消息映射声明和分界宏以及消息映射宏的详细信息，请参阅[消息映射](../../mfc/reference/message-maps-mfc.md)和[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。 有关消息映射范围的详细信息，请参阅[消息映射范围的处理程序](../../mfc/handlers-for-message-map-ranges.md)。

## <a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

开始您的消息映射的定义。

### <a name="syntax"></a>语法

```
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>parameters

*类*<br/>
指定其消息映射所属的类的名称。

*baseClass*<br/>
指定*类*的基类的名称。

### <a name="remarks"></a>备注

在定义类的成员函数的实现（.cpp）文件中，启动带有 BEGIN_MESSAGE_MAP 宏的消息映射，然后为每个消息处理函数添加宏项，并通过 END_MESSAGE_MAP 完成消息映射。宏定义.

有关消息映射的详细信息，请参阅[消息映射](message-maps-mfc.md)

### <a name="example"></a>示例

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

开始对包含单个模板参数的类类型的消息映射的定义。

### <a name="syntax"></a>语法

```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>parameters

*类*<br/>
指定其消息映射所属的类的名称。

type_name<br/>
为类指定的模板参数的名称。

*baseClass*<br/>
指定*类*的基类的名称。

### <a name="remarks"></a>备注

此宏类似于[BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map)宏;但是，此宏适用于包含单个模板参数的类。

在类的 "方法实现" 部分中，用 BEGIN_TEMPLATE_MESSAGE_MAP 宏启动消息映射;然后添加每个消息处理程序方法的宏条目，就像对标准消息映射进行的那样。 与 BEGIN_MESSAGE_MAP 宏一样，用[END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map)宏来完成模板消息映射。

有关实现模板类的消息映射的详细信息，请参阅[如何：为模板类创建消息映射](../how-to-create-a-message-map-for-a-template-class.md)。

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="declare_message_map"></a>DECLARE_MESSAGE_MAP

声明类定义消息映射。 程序中的每个 `CCmdTarget`派生类必须提供消息映射来处理消息。

### <a name="syntax"></a>语法

```
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>备注

在类声明的末尾使用 DECLARE_MESSAGE_MAP 宏。 然后，在定义类的成员函数的 .cpp 文件中，使用 BEGIN_MESSAGE_MAP 宏、每个消息处理函数的宏项和 END_MESSAGE_MAP 的宏。

> [!NOTE]
>  如果在 DECLARE_MESSAGE_MAP 后声明任何成员，则必须为它们指定新的访问类型（**公共**、**私有**或**受保护**）。

有关消息映射和 DECLARE_MESSAGE_MAP 宏的详细信息，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>示例

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="end_message_map"></a>END_MESSAGE_MAP

结束消息映射的定义。

### <a name="syntax"></a>语法

```
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>备注

有关消息映射和 END_MESSAGE_MAP 宏的详细信息，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="on_command"></a>ON_COMMAND

此宏将命令消息映射到成员函数。

### <a name="syntax"></a>语法

```
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>parameters

*commandId*<br/>
命令 ID。

*memberFxn*<br/>
命令映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

它指示哪个函数将处理命令用户界面对象（如菜单项或工具栏按钮）的命令消息。

当命令目标对象收到具有指定 ID 的 Windows WM_COMMAND 消息时，ON_COMMAND 将调用成员函数 `memberFxn` 来处理该消息。

使用 ON_COMMAND 将单个命令映射到成员函数。 使用[ON_COMMAND_RANGE](#on_command_range)将一系列命令 id 映射到一个成员函数。 只有一个消息映射项可以匹配给定的命令 ID。 也就是说，不能将命令映射到多个处理程序。 有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>示例

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>要求

**标头：** afxmsg_。h

## <a name="on_command_ex"></a>ON_COMMAND_EX

扩展命令处理程序成员函数。

### <a name="syntax"></a>语法

```
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>parameters

*commandId*<br/>
命令 ID。

*memberFxn*<br/>
命令映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

命令消息处理程序的扩展形式可用于高级用途。 ON_COMMAND_EX 宏用于此类消息处理程序，并提供[ON_COMMAND](message-map-macros-mfc.md#on_command)功能的超集。 扩展命令处理程序成员函数采用单个参数，即包含命令 ID 的 UINT，并返回一个布尔值。 返回值应为 TRUE 以指示该命令已处理;否则，路由将继续其他命令目标对象。

有关详细信息，请参阅技术说明 [TN006：消息映射] tm006-maps.md）。

### <a name="requirements"></a>要求

头文件： afxmsg_。h

## <a name="on_control"></a>ON_CONTROL

指示哪个函数将处理自定义控件通知消息。

### <a name="syntax"></a>语法

```
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>parameters

*此接通 wnotifycode*<br/>
控件的通知代码。

*commandId*<br/>
命令 ID。

*memberFxn*<br/>
命令映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

控件通知消息是从控件发送到其父窗口的消息。

消息映射中应只有一个 ON_CONTROL 宏语句，以便每个必须映射到消息处理程序函数的控件通知消息。

有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>要求

**标头：** afxmsg_。h

## <a name="on_message"></a>ON_MESSAGE

指示哪个函数将处理用户定义的消息。

### <a name="syntax"></a>语法

```
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>parameters

message<br/>
消息 ID。

*memberFxn*<br/>
消息映射到的消息处理程序函数的名称。

函数的类型必须是 `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`。

### <a name="remarks"></a>备注

用户定义消息是任何非标准 Windows WM_MESSAGE 消息的消息。 选择消息 ID 时，必须使用 WM_USER （0x0400）范围内的值才能0x7FFF 或 WM_APP （0x8000）到0xBFFF。 有关消息 Id 的详细信息，请参阅[WM_APP](/windows/win32/winmsg/wm-app)。

消息映射中应该只有一个 ON_MESSAGE 宏语句，这些语句必须映射到消息处理程序函数。

> [!NOTE]
>  除了用户定义的消息以外，ON_MESSAGE 处理不太常见的 Windows 消息。 有关详细信息，请参阅[消息映射](../../mfc/tn006-message-maps.md)。

有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)和[用户定义的处理程序](user-defined-handlers.md)

### <a name="example"></a>示例

```cpp
#define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd2, CWnd)
   ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()

// inside the class declaration
afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

LRESULT CMyWnd2::OnMyMessage(WPARAM wParam, LPARAM lParam)
{
   UNREFERENCED_PARAMETER(wParam);
   UNREFERENCED_PARAMETER(lParam);

   // Handle message here.

   return 0;
}
```

### <a name="requirements"></a>要求

**标头：** afxmsg_。h

## <a name="on_olecmd"></a>ON_OLECMD

通过命令调度接口 `IOleCommandTarget`路由命令。

### <a name="syntax"></a>语法

```
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>parameters

*pguid*<br/>
命令所属的命令组的标识符。 对于标准组，请使用 NULL。

*olecmdid*<br/>
OLE 命令的标识符。

*commandId*<br/>
发出命令的资源或对象的菜单 ID、工具栏 ID、按钮 ID 或其他 ID。

### <a name="remarks"></a>备注

`IOleCommandTarget` 允许容器接收源自 DocObject 的用户界面的命令，并允许容器在 "文件" 菜单上发送相同的命令（如 "新建"、"打开"、"另存" 和 "打印"，并在 "编辑" 菜单上复制、粘贴、撤消等）到 DocObject。

`IOleCommandTarget` 比 OLE 自动化的 `IDispatch`简单。 `IOleCommandTarget` 完全依赖于一组标准的命令，这些命令很少具有参数，也不涉及任何类型信息（对于命令参数，类型安全也会降低）。 如果确实需要调度带有参数的命令，请使用[COleServerDoc：： OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)。

`IOleCommandTarget` 标准菜单命令已由 MFC 在以下宏中实现：

**ON_OLECMD_CLEARSELECTION （）**

调度 "编辑清除" 命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY （）**

调度编辑复制命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT （）**

调度 "编辑剪切" 命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW （）**

调度 File New 命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN （）**

调度文件打开命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP （）**

调度文件页面设置命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE （）**

调度 "编辑粘贴" 命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL （）**

调度 "编辑" "选择性粘贴" 命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT （）**

调度文件打印命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW （）**

调度文件 "打印预览" 命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO （）**

调度编辑重做命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE （）**

调度文件保存命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS （）**

调度文件的 "另存为" 命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS （）**

调度 "文件另存为" 命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL （）**

调度 "编辑全部选择" 命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO （）**

调度 "编辑" 撤消命令。 实现方式：

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>要求

**标头：** afxdocob

## <a name="on_registered_message"></a>ON_REGISTERED_MESSAGE

Windows `RegisterWindowMessage` 函数用于定义在整个系统中保证唯一的新窗口消息。

### <a name="syntax"></a>语法

```
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>parameters

*nMessageVariable*<br/>
已注册的窗口消息 ID 变量。

*memberFxn*<br/>
消息映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

此宏指示哪个函数将处理已注册的消息。

有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>示例

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>要求

**标头：** afxmsg_。h

## <a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

指示哪个函数将处理 Windows RegisterWindowMessage 函数注册的消息。

### <a name="syntax"></a>语法

```
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>parameters

*nMessageVariable*<br/>
已注册的窗口消息 ID 变量。

*memberFxn*<br/>
消息映射到的 CWinThread 函数的名称。

### <a name="remarks"></a>备注

RegisterWindowMessage 用于定义在整个系统中保证唯一的新窗口消息。 CWinThread 类时，必须使用 ON_REGISTERED_THREAD_MESSAGE 而不是 ON_REGISTERED_MESSAGE。

### <a name="requirements"></a>要求

**标头：** afxmsg_。h

## <a name="on_thread_message"></a>ON_THREAD_MESSAGE

指示哪个函数将处理用户定义的消息。

### <a name="syntax"></a>语法

```
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>parameters

message<br/>
消息 ID。

*memberFxn*<br/>
消息映射到的 `CWinThread`消息处理程序函数的名称。

### <a name="remarks"></a>备注

如果有 `CWinThread` 类，则必须使用 ON_THREAD_MESSAGE 而不是 ON_MESSAGE。 用户定义消息是任何非标准 Windows WM_MESSAGE 消息的消息。 消息映射中应该只有一个 ON_THREAD_MESSAGE 宏语句，这些语句必须映射到消息处理程序函数。

### <a name="requirements"></a>要求

**标头：** afxole

## <a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI

此宏指示哪个函数将处理用户界面更新命令消息。

### <a name="syntax"></a>语法

```
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>parameters

*messageId*<br/>
消息 ID。

*memberFxn*<br/>
消息映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

消息映射中应只有一个 ON_UPDATE_COMMAND_UI 宏语句，才能将必须映射到消息处理程序函数的每个用户界面更新命令。

有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>要求

**标头：** afxole

## <a name="on_command_range"></a>ON_COMMAND_RANGE

使用此宏可将一系列连续的命令 Id 映射到单个消息处理程序函数。

### <a name="syntax"></a>语法

```
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>parameters

*id1*<br/>
命令 id 连续范围开头的命令 ID。

*id2*<br/>
命令 id 连续范围末尾的命令 ID。

*memberFxn*<br/>
命令映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

Id 范围从*id1*开始，以*id2*结束。

使用 ON_COMMAND_RANGE 将一系列命令 Id 映射到一个成员函数。 使用[ON_COMMAND](#on_command)将单个命令映射到成员函数。 只有一个消息映射项可以匹配给定的命令 ID。 也就是说，不能将命令映射到多个处理程序。 有关映射消息范围的详细信息，请参阅[消息映射范围的处理程序](../../mfc/handlers-for-message-map-ranges.md)。

消息映射范围没有自动支持，因此必须自行放置宏。

### <a name="example"></a>示例

```cpp
// The code fragment below shows how to use ON_COMMAND_RANGE macro
// to map a contiguous range of command IDs to a single message
// handler function (i.e. OnRangeCmds() in the sample below). In
// addition, it also shows how to use CheckMenuRadioItem() to check a
// selected menu item and makes it a radio item.

BEGIN_MESSAGE_MAP(CChildFrame, CMDIChildWnd)
   ON_COMMAND_RANGE(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, &CChildFrame::OnRangeCmds)
END_MESSAGE_MAP()

void CChildFrame::OnRangeCmds(UINT nID)
{
   CMenu* mmenu = AfxGetMainWnd()->GetMenu();
   CMenu* submenu = mmenu->GetSubMenu(5);
   submenu->CheckMenuRadioItem(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3,
      nID, MF_BYCOMMAND);
}
```

### <a name="requirements"></a>要求

**标头：** afxmsg_。h

## <a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE

将一系列连续的命令 Id 映射到单个更新消息处理程序函数。

### <a name="syntax"></a>语法

```
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>parameters

*id1*<br/>
命令 id 连续范围开头的命令 ID。

*id2*<br/>
命令 id 连续范围末尾的命令 ID。

*memberFxn*<br/>
命令映射到的更新消息处理程序函数的名称。

### <a name="remarks"></a>备注

更新消息处理程序将更新与命令关联的菜单项和工具栏按钮的状态。 Id 范围从*id1*开始，以*id2*结束。

消息映射范围没有自动支持，因此必须自行放置宏。

### <a name="requirements"></a>要求

**标头：** afxmsg_。h

## <a name="on_control_range"></a>ON_CONTROL_RANGE

使用此宏可将一系列连续的控件 Id 映射到指定 Windows 通知消息（如 BN_CLICKED）的单个消息处理程序函数。

### <a name="syntax"></a>语法

```
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>parameters

*此接通 wnotifycode*<br/>
处理程序响应的通知代码。

*id1*<br/>
位于一系列连续控件 Id 开头的命令 ID。

*id2*<br/>
连续控件 Id 范围末尾的命令 ID。

*memberFxn*<br/>
控件映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

Id 范围从*id1*开始，以*id2*结束。 对于来自任何映射控件的指定通知，将调用处理程序。

消息映射范围没有自动支持，因此必须自行放置宏。

有关为一系列控件 Id 实现处理函数的详细信息，请参阅[消息映射范围的处理程序](../../mfc/handlers-for-message-map-ranges.md)。

### <a name="requirements"></a>要求

**标头：** afxmsg_。h

## <a name="see-also"></a>另请参阅

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006：消息映射](../tn006-message-maps.md)<br/>
[COleCmdUI 类](colecmdui-class.md)<br/>
[COleServerDoc：： OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[用户定义的处理程序](user-defined-handlers.md)<br/>
[CCmdUI 类](ccmdui-class.md)
