---
title: TN006：消息映射
ms.date: 06/25/2018
f1_keywords:
- vc.messages.maps
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
ms.openlocfilehash: 489db046910cc4b44e381b3f9056cfe8f8b7ccfa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511113"
---
# <a name="tn006-message-maps"></a>TN006：消息映射

此注释描述 MFC 消息映射设施。

## <a name="the-problem"></a>问题

Microsoft Windows 在使用其消息传递功能的窗口类中实现虚函数。 由于涉及大量消息, 为每个窗口消息提供单独的虚函数会创建一个非常大的 vtable。

因为系统定义的 Windows 消息数随时间而变化, 并且应用程序可以定义自己的 Windows 消息, 所以消息映射提供了一个间接程度, 可防止接口更改破坏现有代码。

## <a name="overview"></a>概述

MFC 为在传统的基于 Windows 的程序中使用的 switch 语句提供了一种替代方法, 用于处理发送到窗口的消息。 可以定义从消息到方法的映射, 这样, 当窗口收到消息时, 将自动调用相应的方法。 此消息映射功能旨在类似于虚函数, 但具有C++虚函数无法实现的其他优点。

## <a name="defining-a-message-map"></a>定义消息映射

[DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map)宏为类声明了三个成员。

- 名为 *_messageEntries*的 AFX_MSGMAP_ENTRY 项的专用数组。

- 指向 *_messageEntries*数组的一个名为*messageMap*的受保护的 AFX_MSGMAP 结构。

- 一个名`GetMessageMap`为的受保护虚拟函数, 该函数返回*messageMap*的地址。

此宏应置于使用消息映射的任何类的声明中。 按照约定, 它位于类声明的末尾。 例如：

```cpp
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

这是在创建新类时由程序向导和 ClassWizard 生成的格式。 ClassWizard 需要//{{和//}} 个括号。

消息映射表是通过使用一组扩展到消息映射项的宏来定义的。 表以[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏调用开头, 该调用定义此消息映射处理的类以及未处理消息传递到的父类。 该表以[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)宏调用结束。

在这两个宏调用之间, 是此消息映射要处理的每个消息的条目。 每个标准 Windows 消息都有一个格式为 ON_WM_*MESSAGE_NAME*的宏, 该宏将生成该消息的条目。

已定义标准函数签名, 用于解包每个 Windows 消息的参数并提供类型安全性。 可在[CWnd](../mfc/reference/cwnd-class.md)声明中的 afxwin.h 文件中找到这些签名。 每个标记都用关键字**afx_msg**标记, 以方便识别。

> [!NOTE]
> ClassWizard 要求在消息映射处理程序声明中使用**afx_msg**关键字。

这些函数签名是使用简单约定派生的。 函数名称始终以`"On`"。 后面跟有 "WM_" 的 Windows 消息的名称, 每个单词的首字母都大写。 参数的顺序为*wParam*后`LOWORD`跟 (*lParam*) then `HIWORD`(*lParam*)。 未通过未使用的参数。 由 MFC 类包装的任何句柄都转换为指向相应 MFC 对象的指针。 下面的示例演示如何处理 WM_PAINT 消息并导致`CMyWnd::OnPaint`调用函数:

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

消息映射表必须在任何函数或类定义的范围之外定义。 不应将其放在 extern "C" 块中。

> [!NOTE]
> ClassWizard 将修改在//{{and//} 注释括号之间发生的消息映射条目。

## <a name="user-defined-windows-messages"></a>用户定义的 Windows 消息

用户定义的消息可以通过使用[ON_MESSAGE](reference/message-map-macros-mfc.md#on_message)宏包含在消息映射中。 此宏接受以下形式的消息号和方法:

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

在此示例中, 我们为自定义消息建立了一个处理程序, 该自定义消息具有从标准 WM_USER 基础派生的用户定义消息的 Windows 消息 ID。 下面的示例演示如何调用此处理程序:

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

使用此方法的用户定义消息的范围必须在 WM_USER 到0x7fff 的范围内。

> [!NOTE]
> ClassWizard 不支持从 ClassWizard 用户界面输入 ON_MESSAGE 处理程序例程。 您必须从视觉对象C++编辑器中手动输入。 ClassWizard 将分析这些项, 并允许你像浏览其他任何消息映射项一样浏览这些项。

## <a name="registered-windows-messages"></a>已注册的 Windows 消息

[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)函数用于定义在整个系统中保证唯一的新窗口消息。 宏 ON_REGISTERED_MESSAGE 用于处理这些消息。 此宏接受包含已注册 windows 消息 ID 的*UINT NEAR*变量的名称。 例如

```cpp
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

已注册的 Windows 消息 ID 变量 (在本示例中为 WM_FIND) 必须是*接近*变量, 因为 ON_REGISTERED_MESSAGE 的实现方式。

使用此方法的用户定义消息的范围将在0xC000 到0xFFFF 的范围内。

> [!NOTE]
> ClassWizard 不支持从 ClassWizard 用户界面输入 ON_REGISTERED_MESSAGE 处理程序例程。 您必须从文本编辑器中手动输入这些内容。 ClassWizard 将分析这些项, 并允许你像浏览其他任何消息映射项一样浏览这些项。

## <a name="command-messages"></a>命令消息

来自菜单和加速器的命令消息在带有 ON_COMMAND 宏的消息映射中进行处理。 此宏接受命令 ID 和方法。 只有具有等于指定命令 ID 的*wParam*的特定 WM_COMMAND 消息才能通过消息映射项中指定的方法进行处理。 命令处理程序成员函数不采用任何参数并返回**void**。 宏的格式如下:

```cpp
ON_COMMAND(id, memberFxn)
```

命令更新消息通过相同机制进行路由, 但改为使用 ON_UPDATE_COMMAND_UI 宏。 命令更新处理程序成员函数采用单个参数、指向[CCmdUI](../mfc/reference/ccmdui-class.md)对象的指针并返回**void**。 宏的格式为

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

高级用户可以使用 ON_COMMAND_EX 宏, 该宏是命令消息处理程序的一种扩展形式。 宏提供 ON_COMMAND 功能的超集。 扩展命令处理程序成员函数采用单个参数, 即包含命令 ID 的**UINT** , 并返回一个**布尔**值。 返回值应为**TRUE**以指示已处理该命令。 否则, 路由将继续其他命令目标对象。

这些形式的示例:

- 内部资源 .h (通常由视觉对象C++生成)

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- 在类声明中

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- 在消息映射定义中

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- 在实现文件中

    ```cpp
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

高级用户可以使用单个命令处理程序来处理一系列命令:[ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)或 ON_COMMAND_RANGE_EX。 有关这些宏的详细信息, 请参阅产品文档。

> [!NOTE]
> ClassWizard 支持创建 ON_COMMAND 和 ON_UPDATE_COMMAND_UI 处理程序, 但不支持创建 ON_COMMAND_EX 或 ON_COMMAND_RANGE 处理程序。 但是, 类向导将分析并让您浏览所有四个命令处理程序变量。

## <a name="control-notification-messages"></a>控制通知消息

从子控件发送到窗口的消息在其消息映射项中具有额外的信息: 控件的 ID。 仅当满足以下条件时, 才会调用消息映射条目中指定的消息处理程序:

- 控件通知代码 (高位字, *lParam*) (如 BN_CLICKED) 与消息映射项中指定的通知代码相匹配。

- 控件 ID (*wParam*) 与消息映射项中指定的控件 id 匹配。

自定义控件通知消息可以使用[ON_CONTROL](reference/message-map-macros-mfc.md#on_control)宏来定义带有自定义通知代码的消息映射项。 此宏的格式为

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

对于高级使用[ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) , 可用于处理来自具有相同处理程序的一系列控件的特定控件通知。

> [!NOTE]
> ClassWizard 不支持在用户界面中创建 ON_CONTROL 或 ON_CONTROL_RANGE 处理程序。 必须用文本编辑器手动输入这些内容。 ClassWizard 将分析这些项, 并允许你像浏览其他任何消息映射项一样浏览这些项。

Windows 公共控件使用功能更强大的[WM_NOTIFY](/windows/win32/controls/wm-notify)来实现复杂的控件通知。 此版本的 MFC 通过使用 ON_NOTIFY 和 ON_NOTIFY_RANGE 宏直接支持此新消息。 有关这些宏的详细信息, 请参阅产品文档。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
