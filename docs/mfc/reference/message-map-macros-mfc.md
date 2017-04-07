---
title: "消息映射宏 (MFC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- message map macros
- Windows messages [C++], declaration
- demarcating Windows messages
- message maps [C++], macros
- message maps [C++], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: d4b97ed874b145f9c6d9a9536476243bba0fd1c1
ms.openlocfilehash: 0c5856dce919ca8ea2d396fbf2523dc45409b519
ms.lasthandoff: 03/06/2017

---
# <a name="message-map-macros-mfc"></a>消息映射宏 (MFC)
为了支持消息映射，MFC 提供了以下宏：  
  
### <a name="message-map-declaration-and-demarcation-macros"></a>消息映射声明和分界宏  
  
|||  
|-|-|  
|[DECLARE_MESSAGE_MAP](#declare_message_map)|声明将在类中使用消息映射来将消息映射到函数（必须在类声明中使用）。|  
|[BEGIN_MESSAGE_MAP](#begin_message_map)|开始消息映射的定义（必须在类实现中使用）。|  
|[END_MESSAGE_MAP](#end_message_map)|结束消息映射的定义（必须在类实现中使用）。|  
  
### <a name="message-mapping-macros"></a>消息映射宏  
  
|||  
|-|-|  
|[ON_COMMAND](#on_command)|指示哪个函数将处理指定的命令消息。|  
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
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|指示哪个更新处理程序将处理命令中指定的 Id 的前两个 pa 范围] rameters 宏。|  
|[ON_CONTROL_RANGE](#on_control_range)|指示哪个函数将处理来自在宏的第二个和第三个参数中指定的控件 ID 的范围的通知。 第一个参数是控件通知消息，如**BN_CLICKED**。|  
  
 消息映射、 消息映射声明和分界宏和消息映射宏的详细信息，请参阅[消息映射](../../mfc/reference/message-maps-mfc.md)和[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。 有关消息映射范围的详细信息，请参阅[消息映射范围的处理程序](../../mfc/handlers-for-message-map-ranges.md)。  

## <a name="declare_message_map"></a>DECLARE_MESSAGE_MAP
 声明的类定义的消息映射。 每个`CCmdTarget`-在程序中的派生的类必须提供的消息映射来处理消息。  
  
### <a name="syntax"></a>语法  
  
```    
DECLARE_MESSAGE_MAP( )  
```  
  
### <a name="remarks"></a>备注  
 使用`DECLARE_MESSAGE_MAP`宏在类声明的末尾。 然后，在定义类的成员函数的.cpp 文件，使用`BEGIN_MESSAGE_MAP`宏，宏项，为每个消息处理程序函数，与`END_MESSAGE_MAP`宏。  
  
> [!NOTE]
>  如果您声明后的任何成员`DECLARE_MESSAGE_MAP`，必须指定新的访问类型 (**公共**， `private`，或`protected`) 为它们。  
  
 有关详细信息消息映射和`DECLARE_MESSAGE_MAP`宏，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。  
  
### <a name="example"></a>示例  
```cpp  
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
``` 
  
### <a name="requirements"></a>要求  
 **标头:** afxwin.h  

## <a name="begin_message_map"></a>BEGIN_MESSAGE_MAP
开始消息映射的定义。  
  
### <a name="syntax"></a>语法  
  
```  
BEGIN_MESSAGE_MAP( theClass, baseClass )  
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 指定其消息映射的类的名称。  
  
 `baseClass`  
 指定 `theClass` 的基类的名称。  
  
### <a name="remarks"></a>备注  
 在定义您的类的成员函数的实现 (.cpp) 文件，开始使用消息映射`BEGIN_MESSAGE_MAP`宏，然后为每个消息处理程序函数，添加宏条目并完成用的消息映射`END_MESSAGE_MAP`宏。  
  
 关于消息映射的详细信息，请参阅[消息映射](message-maps-mfc.md)  
  
### <a name="example"></a>示例  
```cpp  
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
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
 有关详细信息消息映射和`END_MESSAGE_MAP`宏，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。  
  
### <a name="requirements"></a>要求  
 **标头:** afxwin.h  

## <a name="on_command"></a>ON_COMMAND
该宏将一条命令消息映射到的成员函数。  
  
### <a name="syntax"></a>语法  
  
```  
ON_COMMAND( id, memberFxn )  
```  
  
### <a name="parameters"></a>参数  
 `id`  
 命令 ID。  
  
 `memberFxn`  
 命令映射到的消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 它指示哪个函数将处理来自一个命令用户界面对象，如菜单项或工具栏按钮的命令消息。  
  
 当命令目标对象接收 Windows **WM_COMMAND**具有指定 ID 的消息`ON_COMMAND`将调用成员函数`memberFxn`来处理该消息。  
  
 使用`ON_COMMAND`要映射到某个成员函数的单个命令。 使用[ON_COMMAND_RANGE](#on_command_range)若要将命令 id 的范围映射到一个成员函数。 只有一个消息映射条目可以匹配给定的命令 id。 也就是说，不能映射到多个处理程序的命令。 有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。  
  
### <a name="example"></a>示例  
```cpp  
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
``` 
  
### <a name="requirements"></a>要求  
 **标头︰** afxmsg_.h  
  
## <a name="on_control"></a>ON_CONTROL
指示哪个函数将处理自定义控件通知消息。  
  
### <a name="syntax"></a>语法  
  
```  
ON_CONTROL( wNotifyCode, id, memberFxn )  
```  
  
### <a name="parameters"></a>参数  
 `wNotifyCode`  
 控件通知代码。  
  
 `id`  
 命令 ID。  
  
 `memberFxn`  
 命令映射到的消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 控件通知消息是从一个控件发送到其父窗口。  
  
 应该有且仅有`ON_CONTROL`宏语句在消息映射中每个控件通知消息，必须映射到消息处理程序函数。  
  
 有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxmsg_.h  
  

## <a name="on_message"></a>ON_MESSAGE  
指示哪个函数将处理用户定义的消息。  
  
### <a name="syntax"></a>语法  
  
```  
ON_MESSAGE( message, memberFxn )  
```  
  
### <a name="parameters"></a>参数  
 `message`  
 消息 ID。  
  
 `memberFxn`  
 消息映射到的消息处理程序函数的名称。  
  
 函数的类型必须是`afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`。  
  
### <a name="remarks"></a>备注  
 用户定义的任何消息不是标准的 Windows`WM_MESSAGE`消息。 如果选择消息 ID，则必须使用的范围内的值`WM_USER`(0x0400) 到 0x7FFF 或`WM_APP`(0x8000) 到 0xBFFF。 有关消息 Id 的详细信息，请参阅[WM_APP](http://msdn.microsoft.com/library/windows/desktop/ms644930)。  
  
 应该有且仅有`ON_MESSAGE`宏语句在消息映射中每个用户定义消息，必须映射到消息处理程序函数。  
  
> [!NOTE]
>  除了用户定义消息，`ON_MESSAGE`处理不太常见的 Windows 消息。 有关详细信息，请参阅知识库文章[99848︰ 信息︰ 使用 ON_MESSAGE() 宏映射不太常见消息](http://go.microsoft.com/fwlink/?linkId=192022)。  
  
 有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)和[用户定义处理程序](user-defined-handlers.md)  
  
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
 **标头︰** afxmsg_.h  

## <a name="on_olecmd"></a>ON_OLECMD    
将命令路由命令调度接口通过`IOleCommandTarget`。  
  
### <a name="syntax"></a>语法  
  
```  
ON_OLECMD( pguid, olecmdid, id )  
```  
  
### <a name="parameters"></a>参数  
 `pguid`  
 此命令所属的命令组的标识符。 使用**NULL**为标准的组。  
  
 *olecmdid*  
 OLE 命令标识符。  
  
 `id`  
 菜单 ID、 工具栏 ID、 按钮 ID 或其他资源或发出命令的对象的 ID。  
  
### <a name="remarks"></a>备注  
 `IOleCommandTarget`允许容器接收源自 DocObject 的用户界面的命令，并允许容器以发送相同的命令 (如新建、 打开、 另存为，和上的文件菜单中; 打印和复制、 粘贴、 撤消，依次类推编辑菜单上) 到 DocObject。  
  
 `IOleCommandTarget`OLE 自动化的比简单得多`IDispatch`。 `IOleCommandTarget`完全依赖于一组标准的命令，它很少能有参数，并且没有类型信息不涉及 （类型安全性降低了命令的参数）。 如果您确实需要调度带参数的命令，使用[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)。  
  
 `IOleCommandTarget`标准菜单命令中已经实现了由 MFC 以下宏︰  
  
 **ON_OLECMD_CLEARSELECTION （)**  
  
 将调度清除编辑命令。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`  
  
 **ON_OLECMD_COPY （)**  
  
 将调度编辑复制命令。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`  
  
 **ON_OLECMD_CUT （)**  
  
 将调度编辑剪切的命令。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`  
  
 **ON_OLECMD_NEW （)**  
  
 将调度文件新的命令。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`  
  
 **ON_OLECMD_OPEN （)**  
  
 将调度文件打开命令。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`  
  
 **ON_OLECMD_PAGESETUP （)**  
  
 将调度文件页安装程序命令。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`  
  
 **ON_OLECMD_PASTE （)**  
  
 将调度编辑粘贴命令。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`  
  
 **ON_OLECMD_PASTESPECIAL （)**  
  
 将调度编辑选择性粘贴命令。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`  
  
 **ON_OLECMD_PRINT （)**  
  
 将文件打印命令进行调度。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`  
  
 **ON_OLECMD_PRINTPREVIEW （)**  
  
 将文件打印预览命令进行调度。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`  
  
 **ON_OLECMD_REDO （)**  
  
 编辑重做命令会将调度。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`  
  
 **ON_OLECMD_SAVE （)**  
  
 将文件另存命令进行调度。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`  
  
 **ON_OLECMD_SAVE_AS （)**  
  
 将文件另存为命令进行调度。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`  
  
 **ON_OLECMD_SAVE_COPY_AS （)**  
  
 将调度文件副本另存为命令。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`  
  
 **ON_OLECMD_SELECTALL （)**  
  
 将调度编辑选择的所有命令。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`  
  
 **ON_OLECMD_UNDO （)**  
  
 将调度编辑撤消命令。 作为实现︰  
  
 `ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`  
  
### <a name="requirements"></a>要求  
 **标头︰** afxdocob.h  
  
### <a name="see-also"></a>另请参阅  
 [COleCmdUI 类](colecmdui-class.md)   
 [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)

## <a name="on_registered_message"></a>ON_REGISTERED_MESSAGE
Windows **RegisterWindowMessage**函数用于定义保证是唯一的在整个系统的新窗口消息。  
  
### <a name="syntax"></a>语法  
  
```  
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )  
```  
  
### <a name="parameters"></a>参数  
 `nMessageVariable`  
 已注册的窗口消息 ID 变量中。  
  
 `memberFxn`  
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
 **标头︰** afxmsg_.h  
  
### <a name="see-also"></a>另请参阅  
 [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)   
 [用户定义的处理程序](user-defined-handlers.md)

## <a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE    
指示哪个函数将处理由 Windows RegisterWindowMessage 函数注册消息。  
  
### <a name="syntax"></a>语法  
  
```  
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )  
```  
  
### <a name="parameters"></a>参数  
 `nMessageVariable`  
 已注册的窗口消息 ID 变量中。  
  
 `memberFxn`  
 消息映射到的 CWinThread 消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 RegisterWindowMessage 用于定义保证是唯一的在整个系统的新窗口消息。 ON_REGISTERED_THREAD_MESSAGE 必须使用而不是 ON_REGISTERED_MESSAGE，当您有一个 CWinThread 类。 
  
### <a name="requirements"></a>要求  
 **标头︰** afxmsg_.h  

## <a name="on_thread_message"></a>ON_THREAD_MESSAGE    
指示哪个函数将处理用户定义的消息。  
  
### <a name="syntax"></a>语法  
  
```  
ON_THREAD_MESSAGE( message, memberFxn )  
```  
  
### <a name="parameters"></a>参数  
 `message`  
 消息 ID。  
  
 `memberFxn`  
 名称`CWinThread`-消息的消息映射处理程序函数。  
  
### <a name="remarks"></a>备注  
 `ON_THREAD_MESSAGE`必须使用而不是`ON_MESSAGE`当具有`CWinThread`类。 用户定义的任何消息不是标准的 Windows **WM_MESSAGE**消息。 应该有且仅有`ON_THREAD_MESSAGE`宏语句在消息映射中每个用户定义消息，必须映射到消息处理程序函数。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxole.h  

## <a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI    
此宏指示哪个函数将处理用户界面更新命令消息。  
  
### <a name="syntax"></a>语法  
  
```  
ON_UPDATE_COMMAND_UI( id, memberFxn )  
```  
  
### <a name="parameters"></a>参数  
 `id`  
 消息 ID。  
  
 `memberFxn`  
 消息映射到的消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 应该有且仅有`ON_UPDATE_COMMAND_UI`在必须映射到消息处理程序函数的每个用户界面更新命令的消息映射宏语句。  
  
 有关详细信息和示例，请参阅[消息处理和映射主题](../../mfc/message-handling-and-mapping.md)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
### <a name="see-also"></a>另请参阅  
 [CCmdUI 类](ccmdui-class.md)

## <a name="on_command_range"></a>ON_COMMAND_RANGE  
使用此宏来将一组连续的命令 Id 映射到单个消息处理程序函数。  
  
### <a name="syntax"></a>语法
  
```  
ON_COMMAND_RANGE( id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>参数  
 `id1`  
 一组连续的命令 Id 开头的命令 ID。  
  
 `id2`  
 在一个连续的命令 Id 范围末尾的命令 ID。  
  
 `memberFxn`  
 命令映射到的消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 Id 范围开头`id1`和结尾`id2`。  
  
 使用`ON_COMMAND_RANGE`若要将命令 Id 的范围映射到一个成员函数。 使用[ON_COMMAND](#on_command)要映射到某个成员函数的单个命令。 只有一个消息映射条目可以匹配给定的命令 id。 也就是说，不能映射到多个处理程序的命令。 消息映射范围的详细信息，请参阅[消息映射范围的处理程序](../../mfc/handlers-for-message-map-ranges.md)。  
  
 没有自动支持的消息映射范围，因此必须亲自将该宏。  
  
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
 **标头︰** afxmsg_.h  

## <a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE    
将一组连续的命令 Id 映射到单个更新消息处理程序函数。  
  
### <a name="syntax"></a>语法  
  
```  
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>参数  
 `id1`  
 一组连续的命令 Id 开头的命令 ID。  
  
 `id2`  
 在一个连续的命令 Id 范围末尾的命令 ID。  
  
 `memberFxn`  
 命令映射到的更新消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 更新处理程序更新菜单项和工具栏按钮与命令关联的状态消息。 Id 范围开头`id1`和结尾`id2`。  
  
 没有自动支持的消息映射范围，因此必须亲自将该宏。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxmsg_.h  

## <a name="on_control_range"></a>ON_CONTROL_RANGE     
使用此宏将一组连续的控件 Id 映射到单个消息处理程序函数为指定的 Windows 通知消息，如**BN_CLICKED**。  
  
### <a name="syntax"></a>语法  
  
```  
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>参数  
 `wNotifyCode`  
 通知代码回复您的处理程序。  
  
 `id1`  
 一组连续的控件 Id 开头的命令 ID。  
  
 `id2`  
 在一个连续的控件 Id 范围末尾的命令 ID。  
  
 `memberFxn`  
 控件映射到的消息处理程序函数的名称。  
  
### <a name="remarks"></a>备注  
 Id 范围开头`id1`和结尾`id2`。 指定通知来自映射控件中的任何调用处理程序。  
  
 没有自动支持的消息映射范围，因此必须亲自将该宏。  
  
 有关实现各种控件 Id 的处理程序函数的详细信息，请参阅[消息映射范围的处理程序](../../mfc/handlers-for-message-map-ranges.md)。  
  
### <a name="requirements"></a>要求  
 **标头︰** afxmsg_.h  
  



