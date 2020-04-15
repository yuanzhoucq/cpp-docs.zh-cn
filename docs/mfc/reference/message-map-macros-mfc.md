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
ms.openlocfilehash: 6e9291f0f39057403bc27c7fe4ff5ca5a82dfe3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356585"
---
# <a name="message-map-macros-mfc"></a>消息映射宏 (MFC)

为了支持消息映射，MFC 提供了以下宏：

### <a name="message-map-declaration-and-demarcation-macros"></a>消息映射声明和分界宏

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|声明将在类中使用消息映射来将消息映射到函数（必须在类声明中使用）。|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|开始消息映射的定义（必须在类实现中使用）。|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|开始在包含单个模板参数的类类型上定义消息映射。 |
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

有关消息映射、消息映射声明和标界宏以及消息映射宏的详细信息，请参阅[消息映射](../../mfc/reference/message-maps-mfc.md)和[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。 有关消息映射范围的详细信息，请参阅[消息映射范围的处理程序](../../mfc/handlers-for-message-map-ranges.md)。

## <a name="begin_message_map"></a><a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

开始定义消息映射。

### <a name="syntax"></a>语法

```cpp
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>参数

*类*<br/>
指定消息映射为该类的类的名称。

*基类*<br/>
指定*类*的基类的名称。

### <a name="remarks"></a>备注

在定义类成员函数的实现 （.cpp） 文件中，使用BEGIN_MESSAGE_MAP宏启动消息映射，然后为每个消息处理程序函数添加宏条目，然后使用END_MESSAGE_MAP宏完成消息映射。

有关消息映射的详细信息，请参阅[消息映射](message-maps-mfc.md)

### <a name="example"></a>示例

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="begin_template_message_map"></a><a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

开始在包含单个模板参数的类类型上定义消息映射。

### <a name="syntax"></a>语法

```cpp
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>参数

*类*<br/>
指定消息映射为该类的类的名称。

*type_name*<br/>
为类指定的模板参数的名称。

*基类*<br/>
指定*类*的基类的名称。

### <a name="remarks"></a>备注

此宏类似于[BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map)宏;但是，此宏适用于包含单个模板参数的类。

在类的方法实现部分中，使用BEGIN_TEMPLATE_MESSAGE_MAP宏启动消息映射;在类中，使用 BEGIN_TEMPLATE_MESSAGE_MAP 宏启动消息映射。然后，像为标准消息映射添加每个消息处理程序方法的宏条目。 与BEGIN_MESSAGE_MAP宏一样，使用[END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map)宏完成模板消息映射。

有关实现模板类的消息映射的详细信息，请参阅[如何：为模板类创建消息映射](../how-to-create-a-message-map-for-a-template-class.md)。

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="declare_message_map"></a><a name="declare_message_map"></a>DECLARE_MESSAGE_MAP

声明类定义消息映射。 程序中`CCmdTarget`的每个派生类必须提供消息映射来处理消息。

### <a name="syntax"></a>语法

```cpp
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>备注

在类声明末尾使用DECLARE_MESSAGE_MAP宏。 然后，在定义类成员函数的 .cpp 文件中，使用BEGIN_MESSAGE_MAP宏、每个消息处理程序函数的宏条目和END_MESSAGE_MAP宏。

> [!NOTE]
> 如果在DECLARE_MESSAGE_MAP后声明任何成员，则必须为其指定新的访问类型（**公共**、**私有**或**受保护**）。

有关消息映射和DECLARE_MESSAGE_MAP宏的详细信息，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>示例

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="end_message_map"></a><a name="end_message_map"></a>END_MESSAGE_MAP

结束消息映射的定义。

### <a name="syntax"></a>语法

```cpp
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>备注

有关消息映射和END_MESSAGE_MAP宏的详细信息，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="on_command"></a><a name="on_command"></a>ON_COMMAND

此宏将命令消息映射到成员函数。

### <a name="syntax"></a>语法

```cpp
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>参数

*命令 Id*<br/>
命令 ID。

*成员Fxn*<br/>
命令映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

它指示哪个函数将处理来自命令用户界面对象（如菜单项或工具栏按钮）的命令消息。

当命令目标对象收到带有指定 ID 的 Windows WM_COMMAND 消息时，ON_COMMAND将调用成员`memberFxn`函数来处理该消息。

使用ON_COMMAND将单个命令映射到成员函数。 使用[ON_COMMAND_RANGE](#on_command_range)将命令指示数范围映射到一个成员函数。 只有一个消息映射条目可以匹配给定的命令 ID。 也就是说，不能将命令映射到多个处理程序。 有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

### <a name="example"></a>示例

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>要求

**标题：** afxmsg_.h

## <a name="on_command_ex"></a><a name="on_command_ex"></a>ON_COMMAND_EX

扩展的命令处理程序成员函数。

### <a name="syntax"></a>语法

```cpp
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>参数

*命令 Id*<br/>
命令 ID。

*成员Fxn*<br/>
命令映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

命令消息处理程序的扩展形式可用于高级用途。 ON_COMMAND_EX宏用于此类消息处理程序，它提供了[ON_COMMAND](message-map-macros-mfc.md#on_command)功能的超集。 扩展的命令处理程序成员函数采用单个参数，一个包含命令 ID 的 UINT，并返回 BOOL。 返回值应为 TRUE，以指示已处理命令;因此，返回值应为 TRUE，以指示该命令已处理。否则路由将继续到其他命令目标对象。

有关详细信息，请参阅技术说明 [TN006：消息映射]tm006 消息-maps.md）。

### <a name="requirements"></a>要求

头文件： afxmsg_.h

## <a name="on_control"></a><a name="on_control"></a>ON_CONTROL

指示哪个函数将处理自定义控制通知消息。

### <a name="syntax"></a>语法

```cpp
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>参数

*wNotifyCode*<br/>
控件的通知代码。

*命令 Id*<br/>
命令 ID。

*成员Fxn*<br/>
命令映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

控件通知消息是从控件发送到其父窗口的消息。

对于必须映射到消息处理程序函数的每个控件通知消息，消息映射中应有一个ON_CONTROL宏语句。

有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>要求

**标题：** afxmsg_.h

## <a name="on_message"></a><a name="on_message"></a>ON_MESSAGE

指示哪个函数将处理用户定义的消息。

### <a name="syntax"></a>语法

```cpp
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>参数

*消息*<br/>
消息 ID。

*成员Fxn*<br/>
消息映射到的消息处理程序函数的名称。

函数的类型必须为`afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`。

### <a name="remarks"></a>备注

用户定义的消息不是标准 Windows WM_MESSAGE消息的任何消息。 选择消息 ID 时，必须使用 WM_USER （0x0400） 到 0x7FFF 或 WM_APP （0x8000） 到 0xBFFF 范围内的值。 有关消息指示的详细信息，请参阅[WM_APP](/windows/win32/winmsg/wm-app)。

对于必须映射到消息处理程序函数的每个用户定义的消息，消息映射中应有一个ON_MESSAGE宏语句。

> [!NOTE]
> 除了用户定义的消息外，ON_MESSAGE处理不太常见的 Windows 消息。 有关详细信息，请参阅[消息映射](../../mfc/tn006-message-maps.md)。

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

**标题：** afxmsg_.h

## <a name="on_olecmd"></a><a name="on_olecmd"></a>ON_OLECMD

通过命令调度接口`IOleCommandTarget`路由命令。

### <a name="syntax"></a>语法

```cpp
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>参数

*普吉德*<br/>
命令所属的命令组的标识符。 对标准组使用 NULL。

*奥莱姆迪*<br/>
OLE 命令的标识符。

*命令 Id*<br/>
发出命令的资源或对象的菜单 ID、工具栏 ID、按钮 ID 或其他 ID。

### <a name="remarks"></a>备注

`IOleCommandTarget`允许容器接收源自 DocObject 用户界面的命令，并允许容器向 DocObject 发送相同的命令（如"新建"、"打开"、"保存"和"在文件"菜单上打印;在"编辑"菜单上复制、粘贴、撤消等）。

`IOleCommandTarget`比 OLE 自动化更简单`IDispatch`。 `IOleCommandTarget`完全依赖于一组很少有参数的标准命令，并且不涉及类型信息（命令参数的类型安全性也降低）。 如果确实需要使用参数调度命令，请使用[COleServerDoc：：OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)。

`IOleCommandTarget`标准菜单命令已由 MFC 在以下宏中实现：

**ON_OLECMD_CLEARSELECTION）**

调度编辑清除命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY）**

调度编辑复制命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT）**

调度"编辑剪切"命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW）**

调度文件新命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN）**

调度文件打开命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP）**

调度文件页设置命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE）**

调度编辑粘贴命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL）**

调度编辑粘贴特殊命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT）**

调度文件打印命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW）**

调度文件打印预览命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO）**

调度编辑重做命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE）**

调度文件保存命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS）**

调度文件保存为命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS）**

调度文件保存副本作为命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL）**

调度"编辑选择全部"命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO）**

调度编辑撤消命令。 实施方式如下：

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>要求

**标题：** afxdocob.h

## <a name="on_registered_message"></a><a name="on_registered_message"></a>ON_REGISTERED_MESSAGE

Windows`RegisterWindowMessage`函数用于定义保证在整个系统中唯一的新窗口消息。

### <a name="syntax"></a>语法

```cpp
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>参数

*nMessageVariable*<br/>
已注册的窗口消息 ID 变量。

*成员Fxn*<br/>
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

**标题：** afxmsg_.h

## <a name="on_registered_thread_message"></a><a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

指示哪个函数将处理 Windows 注册窗口消息功能注册的消息。

### <a name="syntax"></a>语法

```cpp
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>参数

*nMessageVariable*<br/>
已注册的窗口消息 ID 变量。

*成员Fxn*<br/>
消息映射到的 CWinThread 消息处理程序函数的名称。

### <a name="remarks"></a>备注

注册窗口消息用于定义保证在整个系统中唯一的新窗口消息。 当您有 CWinThread 类时，必须使用 ON_REGISTERED_THREAD_MESSAGE而不是ON_REGISTERED_MESSAGE。

### <a name="requirements"></a>要求

**标题：** afxmsg_.h

## <a name="on_thread_message"></a><a name="on_thread_message"></a>ON_THREAD_MESSAGE

指示哪个函数将处理用户定义的消息。

### <a name="syntax"></a>语法

```cpp
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>参数

*消息*<br/>
消息 ID。

*成员Fxn*<br/>
消息映射到的`CWinThread`-消息处理程序函数的名称。

### <a name="remarks"></a>备注

当您有`CWinThread`类时，必须使用ON_THREAD_MESSAGE而不是ON_MESSAGE。 用户定义的消息不是标准 Windows WM_MESSAGE消息的任何消息。 对于必须映射到消息处理程序函数的每个用户定义的消息，消息映射中应有一个ON_THREAD_MESSAGE宏语句。

### <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="on_update_command_ui"></a><a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI

此宏指示哪个函数将处理用户界面更新命令消息。

### <a name="syntax"></a>语法

```cpp
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>参数

*消息 Id*<br/>
消息 ID。

*成员Fxn*<br/>
消息映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

对于必须映射到消息处理程序函数的每个用户界面更新命令，消息映射中应有一个ON_UPDATE_COMMAND_UI宏语句。

有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。

### <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="on_command_range"></a><a name="on_command_range"></a>ON_COMMAND_RANGE

使用此宏将连续范围的命令指示数映射到单个消息处理程序函数。

### <a name="syntax"></a>语法

```cpp
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>参数

*id1*<br/>
连续命令 ID 范围开头的命令 ID。

*id2*<br/>
连续命令 ID 范围末尾的命令 ID。

*成员Fxn*<br/>
命令映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

ID 的范围从*id1*开始，以*id2*结尾。

使用ON_COMMAND_RANGE将命令指示数范围映射到一个成员函数。 使用[ON_COMMAND](#on_command)将单个命令映射到成员函数。 只有一个消息映射条目可以匹配给定的命令 ID。 也就是说，不能将命令映射到多个处理程序。 有关映射消息范围的详细信息，请参阅[消息映射范围的处理程序](../../mfc/handlers-for-message-map-ranges.md)。

没有自动支持消息映射范围，因此您必须自己放置宏。

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

**标题：** afxmsg_.h

## <a name="on_update_command_ui_range"></a><a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE

将连续范围的命令指示映射到单个更新消息处理程序函数。

### <a name="syntax"></a>语法

```cpp
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>参数

*id1*<br/>
连续命令 ID 范围开头的命令 ID。

*id2*<br/>
连续命令 ID 范围末尾的命令 ID。

*成员Fxn*<br/>
命令映射到的更新消息处理程序函数的名称。

### <a name="remarks"></a>备注

更新消息处理程序更新与命令关联的菜单项和工具栏按钮的状态。 ID 的范围从*id1*开始，以*id2*结尾。

没有自动支持消息映射范围，因此您必须自己放置宏。

### <a name="requirements"></a>要求

**标题：** afxmsg_.h

## <a name="on_control_range"></a><a name="on_control_range"></a>ON_CONTROL_RANGE

使用此宏可将连续控件 I 范围映射到指定 Windows 通知消息的单个消息处理程序函数，如BN_CLICKED。

### <a name="syntax"></a>语法

```cpp
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>参数

*wNotifyCode*<br/>
处理程序正在响应的通知代码。

*id1*<br/>
连续控制 ID 范围开头的命令 ID。

*id2*<br/>
连续控制 ID 范围末尾的命令 ID。

*成员Fxn*<br/>
将控件映射到的消息处理程序函数的名称。

### <a name="remarks"></a>备注

ID 的范围从*id1*开始，以*id2*结尾。 对于来自任何映射的控件的指定通知，调用处理程序。

没有自动支持消息映射范围，因此您必须自己放置宏。

有关实现一系列控件 I 的处理程序函数的详细信息，请参阅[消息映射范围的处理程序](../../mfc/handlers-for-message-map-ranges.md)。

### <a name="requirements"></a>要求

**标题：** afxmsg_.h

## <a name="see-also"></a>另请参阅

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006：消息映射](../tn006-message-maps.md)<br/>
[COleCmdUI 类](colecmdui-class.md)<br/>
[COleServerDoc：：OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[注册窗口消息](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[用户定义的处理程序](user-defined-handlers.md)<br/>
[CmDUI 类](ccmdui-class.md)
