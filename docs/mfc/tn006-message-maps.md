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
ms.openlocfilehash: 91d1793999c12951bd80e0f592772bbae1e2d679
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463292"
---
# <a name="tn006-message-maps"></a>TN006：消息映射

此注释描述 MFC 消息映射工具。

## <a name="the-problem"></a>问题

Microsoft Windows 中使用其消息传递功能的窗口类实现虚函数。 由于所涉及的消息数过大，为每个 Windows 消息提供单独的虚拟函数会创建非常大的 vtable。

由于系统定义的 Windows 消息数随时间，变化和应用程序可以定义自己的 Windows 消息，因为消息映射提供一定程度的间接性，以防止界面更改破坏现有代码。

## <a name="overview"></a>概述

MFC 提供了用于在传统的基于 Windows 的程序中处理消息发送到的窗口在 switch 语句的替代方法。 可以定义从消息到方法的映射，以便当窗口收到一条消息时，自动调用适当的方法。 此消息映射工具专为类似于虚函数，但还有其他好处不可能具有 c + + 虚函数。

## <a name="defining-a-message-map"></a>定义消息映射

[DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map)宏声明为类的三个成员。

- 调用的专用数组的 AFX_MSGMAP_ENTRY 条目 *_messageEntries*。

- 受保护的 AFX_MSGMAP 结构称为*messageMap* ，指向 *_messageEntries*数组。

- 一种受保护虚拟函数调用`GetMessageMap`返回的地址*messageMap*。

应使用消息映射的任何类声明中放置此宏。 按照约定，它在类声明的末尾处。 例如：

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

这是在创建新的类时，由 AppWizard 和 ClassWizard 生成的格式。 / / {{和 / /}} 方括号所需的类向导。

使用一组扩展到的消息映射条目的宏来定义消息映射的表。 表的前[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏调用中，它将处理此消息映射的类和未处理的消息传递到父类定义。 表结尾[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)宏调用。

两个宏多次调用之间是为每个消息来处理此消息映射条目。 每个标准 Windows 消息具有窗体 ON_WM_ 宏*MESSAGE_NAME* ，用来生成该消息的条目。

标准函数签名定义解压缩每个 Windows 消息的参数和提供类型安全。 可能会在声明中的文件 Afxwin.h 中找到这些签名的[CWnd](../mfc/reference/cwnd-class.md)。 每个标有关键字**afx_msg**以便于识别。

> [!NOTE]
> 类向导要求您使用**afx_msg**消息映射处理程序声明中的关键字。

通过使用简单约定来自这些函数签名。 该函数的名称始终以开头`"On`"。 这被跟"WM_"中删除的 Windows 消息的名称和每个单词首字母大写的第一个字母。 参数的顺序*wParam*跟`LOWORD`(*lParam*) 然后`HIWORD`(*lParam*)。 不传递未使用的参数。 任何由 MFC 类包装的句柄将转换为指向相应的 MFC 对象的指针。 下面的示例演示如何处理 WM_PAINT 消息和导致`CMyWnd::OnPaint`要调用的函数：

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

消息映射表必须定义之外的任何函数或类定义的范围。 它不应将放在 extern"C"块中。

> [!NOTE]
> ClassWizard 将修改消息映射条目之间发生的 / / {{和 / /}} 注释括号。

## <a name="user-defined-windows-messages"></a>用户定义的 Windows 消息

可以通过使用消息映射中包含用户定义的消息[ON_MESSAGE](reference/message-map-macros-mfc.md#on_message)宏。 此宏接受一个消息号和窗体的方法：

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

在此示例中，我们建立具有派生自标准 WM_USER 基本的用户定义消息的 Windows 消息 ID 的自定义消息的处理程序。 下面的示例演示如何调用此处理程序：

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

使用此方法的用户定义消息的范围必须是介于 WM_USER 到 0x7fff。

> [!NOTE]
> 类向导不支持从类向导用户界面的输入 ON_MESSAGE 处理程序例程。 您必须手动输入这些在 Visual c + + 编辑器中。 类向导将分析这些条目，并可以就像任何其他消息映射条目一样对其进行浏览。

## <a name="registered-windows-messages"></a>已注册的 Windows 消息

[RegisterWindowMessage](https://msdn.microsoft.com/library/windows/desktop/ms644947)函数用于定义新的窗口消息来保证是唯一的在整个系统。 ON_REGISTERED_MESSAGE 宏用于处理这些消息。 此宏接受的名称*UINT 附近*变量，其中包含已注册的 windows 消息 id。 例如

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

已注册的 Windows 消息 ID 变量 (在此示例中 WM_FIND) 必须是*NEAR* ON_REGISTERED_MESSAGE 实现的变量的方式。

使用此方法的用户定义消息的范围将 0xC000 到 0xFFFF 范围内。

> [!NOTE]
> 类向导不支持从类向导用户界面的输入 ON_REGISTERED_MESSAGE 处理程序例程。 您必须手动输入这些文本编辑器中。 类向导将分析这些条目，并可以就像任何其他消息映射条目一样对其进行浏览。

## <a name="command-messages"></a>命令消息

在与 ON_COMMAND 宏保持一致的消息映射中处理来自菜单和快捷键的命令消息。 此宏接受命令 ID 和方法。 仅特定 WM_COMMAND 消息具有*wParam*等于指定的命令 ID 进行处理的消息映射项中指定的方法。 命令处理程序成员函数不带任何参数并返回**void**。 该宏具有以下形式：

```cpp
ON_COMMAND(id, memberFxn)
```

命令更新消息相同的机制，通过路由，但改为使用 ON_UPDATE_COMMAND_UI 宏。 命令更新处理程序成员函数采用单个参数，一个指向[CCmdUI](../mfc/reference/ccmdui-class.md)对象，并返回**void**。 该宏采用以下格式

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

高级的用户可以使用 ON_COMMAND_EX 宏，这是命令消息处理程序的扩展的形式。 该宏提供 ON_COMMAND 功能的超集。 扩展的命令处理程序成员函数采用一个参数， **UINT** ，其中包含的命令 ID，返回**BOOL**。 返回值应为 **，则返回 TRUE**以指示已处理该命令。 否则路由到其他命令目标对象将继续。

这些窗体的示例：

- 深入了解 Resource.h （通常由 Visual c + + 生成）

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

高级的用户可以通过使用单个命令处理程序处理一系列命令： [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)或 ON_COMMAND_RANGE_EX。 请参阅有关这些宏的详细信息的产品文档。

> [!NOTE]
> 类向导支持创建 ON_COMMAND 和 ON_UPDATE_COMMAND_UI 处理程序，但它不支持创建 ON_COMMAND_EX 或 ON_COMMAND_RANGE 处理程序。 但是，类向导将分析，以便可以浏览所有四个命令处理程序变体。

## <a name="control-notification-messages"></a>控件通知消息

发送到窗口的子控件从具有一个额外位其消息中的信息的消息映射条目： 控件的 id。 只有在满足以下条件时调用消息映射项中指定的消息处理程序：

- 控件通知代码 (高位字*lParam*)，如 BN_CLICKED，匹配的消息映射条目中指定的通知代码。

- 控件 ID (*wParam*) 匹配的消息映射条目中指定的控件 ID。

可以使用自定义控件通知消息[ON_CONTROL](reference/message-map-macros-mfc.md#on_control)宏来定义的消息映射条目和自定义通知代码。 此宏采用以下格式

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

有关高级用法[ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)可用于处理从一系列具有相同的处理程序的控件的特定控件通知。

> [!NOTE]
> 类向导不支持在用户界面中创建一个 ON_CONTROL 或 ON_CONTROL_RANGE 处理程序。 您必须手动输入这些使用文本编辑器。 类向导将分析这些条目，并可以就像任何其他消息映射条目一样对其进行浏览。

Windows 公共控件使用功能更强大[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)为复杂控件通知。 此版本的 MFC 通过使用和 ON_NOTIFY_RANGE 宏提供直接支持此新消息。 请参阅有关这些宏的详细信息的产品文档。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
