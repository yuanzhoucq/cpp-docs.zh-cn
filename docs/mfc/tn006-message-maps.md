---
title: "TN006：消息映射 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.messages.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "消息映射 [C++], Windows 消息传递"
  - "ON_COMMAND 宏"
  - "ON_COMMAND_EX 宏"
  - "ON_COMMAND_RANGE 宏"
  - "ON_COMMAND_RANGE_EX 宏"
  - "ON_CONTROL 宏"
  - "ON_CONTROL_RANGE 宏"
  - "ON_MESSAGE 宏"
  - "ON_NOTIFY 消息"
  - "ON_NOTIFY_RANGE 宏"
  - "ON_REGISTERED_MESSAGE 宏"
  - "ON_UPDATE_COMMAND_UI 宏"
  - "TN006"
  - "Windows 消息 [C++], 消息映射"
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
caps.latest.revision: 16
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN006：消息映射
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此注释说明 MFC 消息映射功能。  
  
## 问题  
 Microsoft Windows 中使用实现设备其消息的窗口类中的虚函数。  由于涉及大量的消息，提供单独虚函数为每个 Windows 消息将创建一禁止将大 vtable。  
  
 由于系统定义的窗口消息的数量随时间更改，因此，应用程序所以能定义自己的窗口消息，消息映射提供防止中断现有代码的接口更改的间接寻址。  
  
## 概述  
 MFC 提供替代在传统 Windows 程序处理发送到 Windows 的 switch 语句。  映射从消息给方法中定义，这样，当信息由窗口时，收到相应的方法自动调用。  此消息映射功能设计类似于虚函数，但对 C\+\+ 虚拟函数无好处。  
  
## 定义消息映射  
 [DECLARE\_MESSAGE\_MAP](../Topic/DECLARE_MESSAGE_MAP.md) 宏声明类的三个成员。  
  
-   某些私有 `AFX_MSGMAP_ENTRY` 项调用 `_messageEntries`。  
  
-   指向 `_messageEntries` 数组的受保护的 `AFX_MSGMAP` 结构调用 `messageMap`。  
  
-   返回 `messageMap`地址的受保护的虚函数调用 `GetMessageMap`。  
  
 在任何类中声明应将使用消息映射，则此宏。  按照约定，其在类声明结尾处。  例如：  
  
```  
class CMyWnd : public CMyParentWndClass  
{  
    // my stuff...  
  
protected:  
    //{{AFX_MSG(CMyWnd)  
    afx_msg void OnPaint();  
    //}}AFX_MSG  
  
    DECLARE_MESSAGE_MAP()  
};  
```  
  
 在创建新类时，这是 AppWizard ClassWizard 和生成的格式。  \/\/{和}括号 ClassWizard 为\/\/需要的。  
  
 消息映射中的表是使用扩展到的一组消息映射项宏。  使用 [BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md) 宏调用的开始时间表，定义类。此消息映射和父类中处理消息传递。  表与 [END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md) 宏调用结束。  
  
 在这两宏调用之间是此消息映射要处理的每条消息的项。  每个标准 Windows 消息具有生成该消息的项窗体 ON\_WM\_*MESSAGE\_NAME* 的宏。  
  
 一种标准函数签名用于打开每个 Windows 消息参数并提供类型安全定义。  这些签名在 [CWnd](../mfc/reference/cwnd-class.md)声明的文件 Afxwin.h 能找到。  每个标记轻松标识的关键字 `afx_msg`。  
  
> [!NOTE]
>  ClassWizard 需要您在消息映射处理程序声明中使用 `afx_msg` 关键字。  
  
 通过使用简单的约定，这些函数签名中派生的。  始终函数开头的名称用 `"On`”。  这后跟窗口消息。“WM\_”中移除和大写的每个单词的首字母。  排序参数为 `LOWORD`之后的 `wParam` \(`lParam`\) 和 `HIWORD`\(`lParam`\)。  未使用的参数进行传递。  由 MFC 类包装的任何处理转换为对相应的 MFC 对象的指针。  下面的示例演示如何处理 `WM_PAINT` 消息并导致 `CMyWnd::OnPaint` 函数调用：  
  
```  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)  
    //{{AFX_MSG_MAP(CMyWnd)  
    ON_WM_PAINT()  
    //}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 必须定义在任何函数或类定义的范围外，消息映射表。  在外部“C”块不应放置它。  
  
> [!NOTE]
>  ClassWizard 将修改发生在\/\/的消息映射项\/\/{和}注释括号之间。  
  
## 用户定义的窗口消息  
 使用 [ON\_MESSAGE](../Topic/ON_MESSAGE.md) 宏，用户定义消息中可能包含消息映射。  此宏接受一个消息号和窗体的方法：  
  
```  
    // inside the class declaration  
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);  
  
    #define WM_MYMESSAGE (WM_USER + 100)  
  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)  
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)  
END_MESSAGE_MAP()  
```  
  
 在此示例中，我们为与用户定义消息的标准 `WM_USER` 基派生的 Windows 消息 ID 的自定义消息处理程序。  下面的示例演示如何处理事件。  
  
```  
CWnd* pWnd = ...;  
pWnd->SendMessage(WM_MYMESSAGE);  
```  
  
 使用此方法的用户范围定义消息必须在范围的 `WM_USER`。0x7fff。  
  
> [!NOTE]
>  ClassWizard 不支持在 `ON_MESSAGE` 从 ClassWizard 用户界面处理程序的实例。  必须手动输入其从 Visual C\+\+ 编辑器。  ClassWizard 将分析这些输入可浏览他们任何其他消息映射项。  
  
## 已注册窗口消息  
 Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) 函数用于定义确保为唯一的整个系统中的新的 Windows 消息。  `ON_REGISTERED_MESSAGE` 宏来处理这些消息。  此宏接受包含已注册窗口消息标识 `UINT NEAR` 的变量名称  例如  
  
```  
class CMyWnd : public CMyParentWndClass  
{  
public:  
    CMyWnd();  
  
    //{{AFX_MSG(CMyWnd)  
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam);  
    //}}AFX_MSG  
  
    DECLARE_MESSAGE_MAP()  
};  
  
static UINT NEAR WM_FIND = RegisterWindowMessage("COMMDLG_FIND");  
  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)  
    //{{AFX_MSG_MAP(CMyWnd)  
    ON_REGISTERED_MESSAGE(WM_FIND, OnFind)  
    //}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 已注册窗口消息标识变量 \(在此示例中为\) WM\_FIND 必须是 `NEAR` 变量因实现 `ON_REGISTERED_MESSAGE` 的方式。  
  
 使用此方法的用户范围定义消息在范围 0x C000 到 0xFFFF。  
  
> [!NOTE]
>  ClassWizard 不支持在 `ON_REGISTERED_MESSAGE` 从 ClassWizard 用户界面处理程序的实例。  必须手动输入他们从文本编辑器。  ClassWizard 将分析这些输入可浏览他们任何其他消息映射项。  
  
## 命令消息  
 从菜单和快捷键的命令消息与 `ON_COMMAND` 宏的消息映射进行处理。  此宏接受命令 ID 和方法。  存在 `wParam` 等于指定的命令 ID 的特定消息由 `WM_COMMAND` 在消息映射项指定的方法处理。  命令处理程序成员函数不采用任何参数且返回 `void`。  宏具有以下形式：  
  
```  
ON_COMMAND(id, memberFxn)  
```  
  
 命令更新消息通过相同机制传送，但使用 `ON_UPDATE_COMMAND_UI` 宏。  命令更新处理程序成员函数采用单个参数、指向 [CCmdUI](../mfc/reference/ccmdui-class.md) 对象并返回 `void`。  宏有窗体  
  
```  
ON_UPDATE_COMMAND_UI(id, memberFxn)  
```  
  
 高级用户可以使用 `ON_COMMAND_EX` 宏，是命令消息处理程序扩展的窗体。  宏提供 `ON_COMMAND` 功能的扩展。  扩展命令处理程序函数采用成员包含命令 ID 的单个参数，`UINT`，并返回 `BOOL`。  返回值应为 `TRUE` 指示已处理过该命令。  为路由继续将其他命令目标对象。  
  
 这些成员包括：  
  
-   内 Resource.h \(通常发生 Visual C\+\+\)  
  
    ```  
    #define    ID_MYCMD      100  
    #define    ID_COMPLEX    101  
    ```  
  
-   在类声明内部  
  
    ```  
    afx_msg void OnMyCommand();  
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);  
    afx_msg BOOL OnComplexCommand(UINT nID);  
    ```  
  
-   在消息映射中定义  
  
    ```  
    ON_COMMAND(ID_MYCMD, OnMyCommand)  
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)  
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)  
    ```  
  
-   在类实现文件中：  
  
    ```  
    void CMyClass::OnMyCommand()  
    {  
        // handle the command  
    }  
  
    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)  
    {  
        // set the UI state with pCmdUI  
    }  
  
    BOOL CMyClass::OnComplexCommand(UINT nID)  
    {  
        // handle the command  
        return TRUE;  
    }  
    ```  
  
 使用单个命令处理程序，高级用户可以处理范围命令：[ON\_COMMAND\_RANGE](../Topic/ON_COMMAND_RANGE.md) 或 `ON_COMMAND_RANGE_EX`。  有关这些属性的更多信息，请参见 ADO 文档。  
  
> [!NOTE]
>  ClassWizard 支持创建 `ON_COMMAND` 和 `ON_UPDATE_COMMAND_UI` 处理程序，不过，它不支持创建 `ON_COMMAND_EX` 或 `ON_COMMAND_RANGE` 处理程序。  但是，类向导"将分析并可以浏览所有四个命令处理程序的变量。  
  
## 控件通知消息  
 从子发送的消息可向窗口都有多余位信息在他们的消息映射项：控件 ID 的 .  只有在以下条件为真时，在消息映射项指定的消息处理程序添加调用：  
  
-   控件通知代码 \( `lParam`高位字中。\)，如 BN\_CLICKED，与消息映射项指定的通知代码。  
  
-   控件 ID \(`wParam`\) 与消息映射项指定的控件 ID。  
  
 自定义控件通知消息可以使用 [ON\_CONTROL](../Topic/ON_CONTROL.md) 宏定义具有自定义通知代码的消息映射项。  此宏具有窗体  
  
```  
ON_CONTROL(wNotificationCode, id, memberFxn)  
```  
  
 对于高级使用 [ON\_CONTROL\_RANGE](../Topic/ON_CONTROL_RANGE.md) 可用于处理从范围的特定控件通知具有同一处理程序的控件。  
  
> [!NOTE]
>  类向导不支持创建用户界面 \(UI\) 的 `ON_CONTROL` 或 `ON_CONTROL_RANGE` 处理程序。  必须手动输入他们从文本编辑器。  ClassWizard 将分析这些输入可浏览他们任何其他消息映射项。  
  
 Windows 公共控件执行复杂控件通知使用更强大的 [WM\_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)。  通过使用 `ON_NOTIFY` 和 `ON_NOTIFY_RANGE` 宏，此 MFC 版本具有该新的消息直接支持。  有关这些属性的更多信息，请参见 ADO 文档。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)