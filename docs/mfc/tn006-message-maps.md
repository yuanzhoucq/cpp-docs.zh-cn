---
title: "TN006： 消息映射 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.messages.maps
dev_langs:
- C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- ON_NOTIFY_RANGE macro [MFC]
- ON_COMMAND macro [MFC]
- ON_CONTROL_RANGE macro [MFC]
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_NOTIFY message [MFC]
- ON_COMMAND_RANGE_EX macro [MFC]
- ON_MESSAGE macro [MFC]
- Windows messages [MFC], message maps
- ON_COMMAND_RANGE macro [MFC]
- TN006
- ON_CONTROL macro [MFC]
- ON_COMMAND_EX macro [MFC]
- message maps [MFC], Windows messaging
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 567a44cd8d8b979a75eca7647861c579bf0c070b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn006-message-maps"></a>TN006：消息映射
此注释描述 MFC 消息映射工具。  
  
## <a name="the-problem"></a>问题  
 Microsoft Windows 中使用其消息传递功能的窗口类实现虚函数。 由于所涉及的消息数量很多，为每个 Windows 消息提供单独的虚拟函数将创建非常大的 vtable。  
  
 由于系统定义的 Windows 消息数量随着时间推移，更改和应用程序可以定义自己的 Windows 消息，因为消息映射提供一定程度的间接性防止界面将会更改破坏现有代码。  
  
## <a name="overview"></a>概述  
 MFC 提供了用于在传统的基于 Windows 的程序中处理消息发送到窗口 switch 语句的替代方法。 可以定义从消息到方法的映射，这样当窗口收到一条消息时，就会自动调用相应的方法。 此消息映射工具专为类似于虚函数，但还有其他好处不可能具有 c + + 虚函数。  
  
## <a name="defining-a-message-map"></a>定义消息映射  
 [DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map)宏声明为类的三个成员。  
  
-   一个专用的数组`AFX_MSGMAP_ENTRY`条目调用`_messageEntries`。  
  
-   受保护`AFX_MSGMAP`结构调用`messageMap`指向`_messageEntries`数组。  
  
-   一种受保护虚函数调用`GetMessageMap`返回的地址`messageMap`。  
  
 应使用消息映射的任何类声明中放置此宏。 按照约定，它是在类声明的末尾。 例如:  
  
```  
class CMyWnd : public CMyParentWndClass  
{ *// my stuff...  
 
protected: *//{{AFX_MSG(CMyWnd)  
    afx_msg void OnPaint();
*//}}AFX_MSG  
 
    DECLARE_MESSAGE_MAP() 
};  
```  
  
 这是在创建新类时，由 AppWizard 和 ClassWizard 生成的格式。 / / {{和 / /}} ClassWizard 需要括号。  
  
 通过使用一组宏扩展到消息映射项定义的消息映射表。 表开头[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏调用，从而定义的类的此消息映射处理和未经处理的消息传递到的父类。 表结尾[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)宏调用。  
  
 这些两个宏调用之间是为每个消息均由该消息映射条目。 每个标准 Windows 消息具有窗体 ON_WM_ 宏*MESSAGE_NAME* ，用来生成该消息的条目。  
  
 已为解包的每个 Windows 消息的参数并提供类型安全定义了标准函数签名。 可能在声明中的文件 Afxwin.h 中找到这些签名的[CWnd](../mfc/reference/cwnd-class.md)。 用关键字标记每个`afx_msg`以便于识别。  
  
> [!NOTE]
>  ClassWizard 要求你使用`afx_msg`消息映射处理程序声明中的关键字。  
  
 通过使用简单约定来自这些函数的签名。 该函数的名称始终以开头`"On`"。 这被跟与删除"WM_"的 Windows 消息的名称和大小写的每个单词的第一个字母。 参数的顺序是`wParam`跟`LOWORD`(`lParam`) 然后`HIWORD`(`lParam`)。 未使用的参数都不传递。 任何由 MFC 类包装的句柄将转换为指向适当的 MFC 对象的指针。 下面的示例演示如何处理`WM_PAINT`消息和导致`CMyWnd::OnPaint`被调用函数：  
  
```  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass) *//{{AFX_MSG_MAP(CMyWnd)  
    ON_WM_PAINT() *//}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 消息映射表必须定义的任何函数或类定义的作用域之外。 它不应将置于 extern"C"块中。  
  
> [!NOTE]
>  ClassWizard 将修改之间发生的消息映射条目 / / {{和 / /}} 注释括号。  
  
## <a name="user-defined-windows-messages"></a>用户定义的 Windows 消息  
 用户定义的消息可能通过使用包含的消息映射中[ON_MESSAGE](reference/message-map-macros-mfc.md#on_message)宏。 此宏接受消息号和形式的方法：  
  
' * / / 在类声明  
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

 
 #<a name="define-wmmymessage-wmuser--100"></a>定义 WM_MYMESSAGE (WM_USER + 100)  
 
BEGIN_MESSAGE_MAP （CMyWnd，CMyParentWndClass）  
    ON_MESSAGE （WM_MYMESSAGE，OnMyMessage）  
END_MESSAGE_MAP()  
```  
  
 In this example, we establish a handler for a custom message that has a Windows message ID derived from the standard `WM_USER` base for user-defined messages. The following example shows how to call this handler:  
  
```  
CWnd * pWnd =...;  
pWnd-> SendMessage(WM_MYMESSAGE);
```  
  
 The range of user-defined messages that use this approach must be in the range `WM_USER` to 0x7fff.  
  
> [!NOTE]
>  ClassWizard does not support entering `ON_MESSAGE` handler routines from the ClassWizard user interface. You must manually enter them from the Visual C++ editor. ClassWizard will parse these entries and let you browse them just like any other message-map entries.  
  
## Registered Windows Messages  
 The [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) function is used to define a new window message that is guaranteed to be unique throughout the system. The macro `ON_REGISTERED_MESSAGE` is used to handle these messages. This macro accepts a name of a `UINT NEAR` variable that contains the registered windows message ID. For example  
  
```  
类 CMyWnd： 公共 CMyParentWndClass  
{  
public:  
    CMyWnd();

 *//{{AFX_MSG(CMyWnd)  
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam);* //}}AFX_MSG  
 
    DECLARE_MESSAGE_MAP() 
};  
 
静态附近 WM_FIND UINT = RegisterWindowMessage("COMMDLG_FIND");

 
BEGIN_MESSAGE_MAP （CMyWnd，CMyParentWndClass） *//{{AFX_MSG_MAP(CMyWnd)  
    ON_REGISTERED_MESSAGE （WM_FIND，OnFind） * //}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 The registered Windows message ID variable (WM_FIND in this example) must be a `NEAR` variable because of the way `ON_REGISTERED_MESSAGE` is implemented.  
  
 The range of user-defined messages that use this approach will be in the range 0xC000 to 0xFFFF.  
  
> [!NOTE]
>  ClassWizard does not support entering `ON_REGISTERED_MESSAGE` handler routines from the ClassWizard user interface. You must manually enter them from the text editor. ClassWizard will parse these entries and let you browse them just like any other message-map entries.  
  
## Command Messages  
 Command messages from menus and accelerators are handled in message maps with the `ON_COMMAND` macro. This macro accepts a command ID and a method. Only the specific `WM_COMMAND` message that has a `wParam` equal to the specified command ID is handled by the method specified in the message-map entry. Command handler member functions take no parameters and return `void`. The macro has the following form:  
  
```  
ON_COMMAND （id，f x n）  
```  
  
 Command update messages are routed through the same mechanism, but use the `ON_UPDATE_COMMAND_UI` macro instead. Command update handler member functions take a single parameter, a pointer to a [CCmdUI](../mfc/reference/ccmdui-class.md) object, and return `void`. The macro has the form  
  
```  
ON_UPDATE_COMMAND_UI （id，f x n）  
```  
  
 Advanced users can use the `ON_COMMAND_EX` macro, which is an extended form of command message handlers. The macro provides a superset of the `ON_COMMAND` functionality. Extended command-handler member functions take a single parameter, a `UINT` that contains the command ID, and return a `BOOL`. The return value should be `TRUE` to indicate that the command has been handled. Otherwise routing will continue to other command target objects.  
  
 Examples of these forms:  
  
-   Inside Resource.h (usually generated by Visual C++)  
  
 ```  
 #<a name="define----idmycmd------100"></a>定义 ID_MYCMD 100  
 #<a name="define----idcomplex----101"></a>定义 ID_COMPLEX 101  
 ```  
  
-   Inside the class declaration  
  
 ```  
    afx_msg void OnMyCommand();
afx_msg void OnUpdateMyCommand (CCmdUI * pCmdUI);

    afx_msg BOOL OnComplexCommand(UINT nID);

 ```  
  
-   Inside the message map definition  
  
 ```  
    ON_COMMAND(ID_MYCMD,
    OnMyCommand)  
    ON_UPDATE_COMMAND_UI(ID_MYCMD,
    OnUpdateMyCommand)  
    ON_COMMAND_EX(ID_MYCMD,
    OnComplexCommand)  
 ```  
  
-   In the implementation file  
  
 ```  
    void CMyClass::OnMyCommand()  
 {* / / 处理命令  
 }  
 
    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)  
 {* / / 设置带 pCmdUI 的 UI 状态  
 }  
 
    BOOL CMyClass::OnComplexCommand(UINT nID)  
 {* / / 处理命令  
    返回 TRUE;  
 }  
 ```  
  
 Advanced users can handle a range of commands by using a single command handler: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) or `ON_COMMAND_RANGE_EX`. See the product documentation for more information about these macros.  
  
> [!NOTE]
>  ClassWizard supports creating `ON_COMMAND` and `ON_UPDATE_COMMAND_UI` handlers, but it does not support creating `ON_COMMAND_EX` or `ON_COMMAND_RANGE` handlers. However, Class Wizard will parse and let you browse all four command handler variants.  
  
## Control Notification Messages  
 Messages that are sent from child controls to a window have an extra bit of information in their message map entry: the control's ID. The message handler specified in a message map entry is called only if the following conditions are true:  
  
-   The control notification code (high word of `lParam`), such as BN_CLICKED, matches the notification code specified in the message-map entry.  
  
-   The control ID (`wParam`) matches the control ID specified in the message-map entry.  
  
 Custom control notification messages may use the [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) macro to define a message map entry with a custom notification code. This macro has the form  
  
```  
ON_CONTROL （wNotificationCode、 id、 f x n）  
```  
  
 For advanced usage [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) can be used to handle a specific control notification from a range of controls with the same handler.  
  
> [!NOTE]
>  ClassWizard does not support creating an `ON_CONTROL` or `ON_CONTROL_RANGE` handler in the user interface. You must manually enter them with the text editor. ClassWizard will parse these entries and let you browse them just like any other message map entries.  
  
 The Windows Common Controls use the more powerful [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) for complex control notifications. This version of MFC has direct support for this new message by using the `ON_NOTIFY` and `ON_NOTIFY_RANGE` macros. See the product documentation for more information about these macros.  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)

