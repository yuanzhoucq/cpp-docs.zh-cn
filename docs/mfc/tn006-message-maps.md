---
title: TN006： 消息映射 |Microsoft 文档
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c4bc820c6b54e055235c1bd29bd55ccfc032c92
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121671"
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

- AFX_MSGMAP_ENTRY 条目的私有数组调用 *_messageEntries*。

- 受保护的 AFX_MSGMAP 结构调用*messageMap*指向 *_messageEntries*数组。

- 一种受保护虚函数调用`GetMessageMap`返回的地址*messageMap*。

应使用消息映射的任何类声明中放置此宏。 按照约定，它是在类声明的末尾。 例如：

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

这是在创建新类时，由 AppWizard 和 ClassWizard 生成的格式。 / / {{和 / /}} ClassWizard 需要括号。

通过使用一组宏扩展到消息映射项定义的消息映射表。 表开头[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏调用，从而定义的类的此消息映射处理和未经处理的消息传递到的父类。 表结尾[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)宏调用。

这些两个宏调用之间是为每个消息均由该消息映射条目。 每个标准 Windows 消息具有窗体 ON_WM_ 宏*MESSAGE_NAME* ，用来生成该消息的条目。

已为解包的每个 Windows 消息的参数并提供类型安全定义了标准函数签名。 可能在声明中的文件 Afxwin.h 中找到这些签名的[CWnd](../mfc/reference/cwnd-class.md)。 用关键字标记每个**afx_msg**以便于识别。

> [!NOTE]
> ClassWizard 要求你使用**afx_msg**消息映射处理程序声明中的关键字。

 通过使用简单约定来自这些函数的签名。 该函数的名称始终以开头`"On`"。 这被跟与删除"WM_"的 Windows 消息的名称和大小写的每个单词的第一个字母。 参数的顺序是*wParam*跟`LOWORD`(*lParam*) 然后`HIWORD`(*lParam*)。 未使用的参数都不传递。 任何由 MFC 类包装的句柄将转换为指向适当的 MFC 对象的指针。 下面的示例演示如何处理 WM_PAINT 消息和导致`CMyWnd::OnPaint`被调用函数：

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

 消息映射表必须定义的任何函数或类定义的作用域之外。 它不应将置于 extern"C"块中。

> [!NOTE]
> ClassWizard 将修改之间发生的消息映射条目 / / {{和 / /}} 注释括号。

## <a name="user-defined-windows-messages"></a>用户定义的 Windows 消息

用户定义的消息可能通过使用包含的消息映射中[ON_MESSAGE](reference/message-map-macros-mfc.md#on_message)宏。 此宏接受消息号和形式的方法：

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

在此示例中，我们将建立的处理程序具有 Windows 消息 ID 从用户定义的消息的标准 WM_USER 基派生的自定义消息。 下面的示例演示如何调用此处理程序：

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

使用此方法的用户定义的消息的范围必须为范围 WM_USER 到 0x7fff。

> [!NOTE]
> ClassWizard 不支持从 ClassWizard 用户界面的输入 ON_MESSAGE 处理程序例程。 你必须手动输入这些从 Visual c + + 编辑器。 ClassWizard 将分析这些条目，以便你就像任何其他消息映射项一样对其进行浏览。

## <a name="registered-windows-messages"></a>已注册的 Windows 消息

[RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)函数用于定义新的窗口消息来保证是唯一的在整个系统。 ON_REGISTERED_MESSAGE 宏用于处理这些消息。 此宏接受名称*UINT 附近*变量包含已注册的 windows 消息 id。 例如

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

已注册的 Windows 消息 ID 变量 (在此示例中的 WM_FIND) 必须*NEAR* ON_REGISTERED_MESSAGE 实现变量由于的方法。

使用此方法的用户定义的消息的范围将 0xC000 到 0xFFFF 范围内。

> [!NOTE]
> ClassWizard 不支持从 ClassWizard 用户界面的输入 ON_REGISTERED_MESSAGE 处理程序例程。 你必须手动输入这些从文本编辑器。 ClassWizard 将分析这些条目，以便你就像任何其他消息映射项一样对其进行浏览。

## <a name="command-messages"></a>命令消息

从菜单和快捷键的命令消息会在与 ON_COMMAND 宏的消息映射中处理。 此宏接受命令 ID 及方法。 仅特定 WM_COMMAND 消息具有*wParam*等于指定的命令 ID 进行处理的消息映射项中指定的方法。 命令处理程序成员函数不带任何参数并返回**void**。 宏具有以下形式：

```cpp
ON_COMMAND(id, memberFxn)
```

命令更新消息通过相同的机制，路由，但改为使用 ON_UPDATE_COMMAND_UI 宏。 命令更新处理程序成员函数采用一个参数指向的指针[CCmdUI](../mfc/reference/ccmdui-class.md)对象，并返回**void**。 宏形式具有窗体

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

高级的用户可以使用 ON_COMMAND_EX 宏，这是命令消息处理程序以扩展的形式。 宏提供 ON_COMMAND 功能的超集。 扩展的命令处理程序成员函数采用一个参数**UINT** ，其中包含的命令 ID，返回**BOOL**。 返回值应为**TRUE**以指示已处理该命令。 否则路由到其他命令目标对象将继续。

这些窗体的示例：

- 内部 Resource.h （通常由 Visual c + + 生成）

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- 在类声明

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- 在消息映射定义

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- 在实现文件

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

 高级的用户可以通过使用单个命令处理程序处理的命令的范围： [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)或 ON_COMMAND_RANGE_EX。 请参阅有关这些宏的详细信息的产品文档。

> [!NOTE]
> ClassWizard 支持创建 ON_COMMAND 和 ON_UPDATE_COMMAND_UI 处理程序，但它不支持创建 ON_COMMAND_EX 或 ON_COMMAND_RANGE 处理程序。 但是，类向导将分析，以便你浏览所有四个命令处理程序的变体。

## <a name="control-notification-messages"></a>控件通知消息

发送到窗口的子控件从具有一个额外位其消息中的信息的消息映射条目： 控件的 id。 只有在满足以下条件时调用一个消息映射条目中指定的消息处理程序：

- 控件通知代码 (的高位字*lParam*)，如 BN_CLICKED，与在消息映射条目中指定的通知代码匹配。

- 控件 ID (*wParam*) 匹配的消息映射条目中指定的控件 ID。

自定义控件通知消息可能会使用[ON_CONTROL](reference/message-map-macros-mfc.md#on_control)宏来定义自定义通知代码与一个消息映射条目。 此宏形式具有窗体

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

有关高级用法[ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)可以用于处理与同一处理程序的控件的范围中的特定控件通知。

> [!NOTE]
> ClassWizard 不支持用户界面中创建一个 ON_CONTROL 或 ON_CONTROL_RANGE 处理程序。 你必须手动输入这些使用文本编辑器。 ClassWizard 将分析这些条目，以便你就像任何其他消息映射项一样对其进行浏览。

Windows 公共控件使用功能更强大[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)复杂控件通知。 此版本的 MFC 通过使用 ON_NOTIFY 和 ON_NOTIFY_RANGE 宏已直接支持此新消息。 请参阅有关这些宏的详细信息的产品文档。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)  
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)  
