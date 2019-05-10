---
title: TN062:Windows 控件的消息反射
ms.date: 06/28/2018
f1_keywords:
- vc.controls.messages
helpviewer_keywords:
- ON_WM_VKEYTOITEM_REFLECT macro [MFC]
- ON_WM_DRAWITEM_REFLECT macro [MFC]
- ON_WM_VSCROLL_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT message [MFC]
- ON_CONTROL_REFLECT_EX macro [MFC]
- ON_UPDATE_COMMAND_UI_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT_EX message [MFC]
- ON_WM_HSCROLL_REFLECT macro [MFC]
- message reflection [MFC]
- ON_WM_COMPAREITEM_REFLECT macro [MFC]
- ON_WM_MEASUREITEM_REFLECT macro [MFC]
- ON_NOTIFY message [MFC]
- WM_COMMAND [MFC]
- WM_CTLCOLOR message [MFC]
- TN062 [MFC]
- ON_WM_CHARTOITEM_REFLECT macro [MFC]
- ON_WM_CTLCOLOR_REFLECT macro [MFC]
- ON_WM_DELETEITEM_REFLECT macro [MFC]
- notification messages [MFC]
- ON_WM_PARENTNOTIFY_REFLECT macro [MFC]
- WM_NOTIFY message [MFC]
- ON_CONTROL_REFLECT macro
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
ms.openlocfilehash: aa189eec430d72bef753fef7ebbe9ad929d76c87
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351836"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062:Windows 控件的消息反射

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

此技术说明描述消息反射，MFC 4.0 中的新功能。 它还包含有关如何创建使用消息反射的简单可重用控件。

此技术说明不讨论消息反射，因为它适用于 ActiveX 控件 （以前称为 OLE 控件）。 请参阅文章[ActiveX 控件：Windows 控件子类化](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。

**什么是消息反射**

Windows 控件经常向其父窗口发送通知消息。 例如，许多控件将控制颜色通知消息 （WM_CTLCOLOR 或其一个变体） 发送到其父允许父提供用于绘制控件背景的画笔。

在 Windows 和 MFC 4.0 版之前，父窗口中，通常一个对话框，负责处理这些消息。 这意味着，需要在父窗口的类用于处理消息的代码，它必须在每个类都需要处理该消息中重复。 在以上示例中，每个想要使用自定义背景的控件的对话框必须处理控件颜色通知消息。 它会重复使用代码，如果可能，将处理它自己的背景色编写控件类变得容易得多。

在 MFC 4.0 中，旧机制仍适用，父窗口可以处理通知消息。 此外，但是，MFC 4.0 可简化重复使用，它提供一种称为"消息反射"功能允许在子控件窗口或父窗口中，或两者中处理这些通知消息。 在控件背景的颜色示例中，您现在可以编写自己的背景色设置通过处理反射的 WM_CTLCOLOR 消息的控件类 — 所有这些操作都无需依赖父级。 (请注意，由于 mfc 实现消息反射，因此不通过 Windows，父窗口类必须派生自`CWnd`消息反射，若要运行的。)

较旧版本的 MFC 做类似于消息反射通过虚函数提供的几个消息，例如为所有者描述列表框 （WM_DRAWITEM，等等） 的消息。 新的消息反射机制是通用和一致。

消息反射是与 4.0 之前的 MFC 版本编写的代码向后兼容。

如果提供的特定消息的处理程序或某个范围的消息，在父窗口的类中，它将替代反映相同的消息的消息处理程序中提供不在自己的处理程序中调用基类处理程序函数。 例如，如果在对话框类中处理 WM_CTLCOLOR，您处理将重写任何反射的消息处理程序。

仅当发送这些消息的子控件不具有通过反射的消息处理程序，如果在父窗口类中，提供特定的 WM_NOTIFY 消息或范围的 WM_NOTIFY 消息的处理程序，将调用您的处理程序`ON_NOTIFY_REFLECT()`。 如果使用`ON_NOTIFY_REFLECT_EX()`在消息映射中，消息处理程序可能会或可能不允许的父窗口，以处理消息。 如果处理程序返回**FALSE**，消息将由调用返回时，父**TRUE**不允许要对其进行处理的父级。 请注意在通知消息前进行处理反射的消息。

WM_NOTIFY 消息发送时，该控件提供第一次的机会，若要对其进行处理。 如果任何其他反射的消息发送时，父窗口具有第一次的机会，若要对其进行处理，并且控件将收到反射的消息。 若要执行此操作，它将需要一个处理程序函数和控件的类的消息映射中的相应条目。

反射的消息的消息映射宏是常规通知略有不同： 它具有 *_REFLECT*追加到其常用名称。 例如，以处理 WM_NOTIFY 消息的父代中，您可以使用父项的消息映射中的 ON_NOTIFY 宏。 若要处理反射的消息中的子控件，使用子控件的消息映射中 ON_NOTIFY_REFLECT 宏。 在某些情况下，参数不同，也是。 请注意 ClassWizard 通常可以为您添加的消息映射条目并提供用正确的参数的主干函数实现。

请参阅[TN061:ON_NOTIFY 和 WM_NOTIFY 消息](../mfc/tn061-on-notify-and-wm-notify-messages.md)有关新的 WM_NOTIFY 消息的信息。

**消息映射条目和反射的消息的处理程序函数原型**

若要处理反射的控件通知消息，请使用消息映射宏和下表中列出的函数原型。

通常，ClassWizard 可以为您添加这些消息映射条目，并提供的主干函数实现。 请参阅[为反射消息定义消息处理程序](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)有关如何定义反射消息的处理程序的信息。

若要从消息名称转换为反射的宏名称，前面预置*ON_* 和追加 *_REFLECT*。 例如，WM_CTLCOLOR 变为 ON_WM_CTLCOLOR_REFLECT。 （若要查看可以反映哪些消息，请执行下表中的宏项相反的转换。）

上述规则的三个例外是，如下所示：

- WM_COMMAND 通知宏是 ON_CONTROL_REFLECT。

- ON_NOTIFY_REFLECT WM_NOTIFY 反射的宏。

- ON_UPDATE_COMMAND_UI 反射的宏是 ON_UPDATE_COMMAND_UI_REFLECT。

在每个以上的特殊情况下，必须指定处理程序成员函数的名称。 在其他情况下，必须使用处理程序函数的标准名称。

参数的含义和函数的返回值记录在函数名称或函数名称加上*上*预置。 例如，`CtlColor`中所述`OnCtlColor`。 多个反射的消息处理程序需要比父窗口中的类似处理程序较少的参数。 只需与下表中的文档中的正式参数名称的名称匹配。

|映射条目|函数原型|
|---------------|------------------------|
|**ON_CONTROL_REFLECT(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **( );**|
|**ON_NOTIFY_REFLECT(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **( NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT**<strong>\*</strong> *result* **);**|
|**ON_UPDATE_COMMAND_UI_REFLECT(** `memberFxn` **)**|**afx_msg void** `memberFxn` **( CCmdUI**<strong>\*</strong> `pCmdUI` **);**|
|**ON_WM_CTLCOLOR_REFLECT( )**|**afx_msg HBRUSH CtlColor ( CDC**<strong>\*</strong> `pDC` **, UINT** `nCtlColor` **);**|
|**ON_WM_DRAWITEM_REFLECT( )**|**afx_msg void DrawItem ( LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|
|**ON_WM_MEASUREITEM_REFLECT( )**|**afx_msg void MeasureItem ( LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|
|**ON_WM_DELETEITEM_REFLECT( )**|**afx_msg void DeleteItem ( LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|
|**ON_WM_COMPAREITEM_REFLECT( )**|**afx_msg int CompareItem ( LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|
|**ON_WM_CHARTOITEM_REFLECT( )**|**afx_msg int CharToItem ( UINT** `nKey` **, UINT** `nIndex` **);**|
|**ON_WM_VKEYTOITEM_REFLECT( )**|**afx_msg int VKeyToItem ( UINT** `nKey` **, UINT** `nIndex` **);**|
|**ON_WM_HSCROLL_REFLECT( )**|**afx_msg void HScroll ( UINT** `nSBCode` **, UINT** `nPos` **);**|
|**ON_WM_VSCROLL_REFLECT( )**|**afx_msg void VScroll ( UINT** `nSBCode` **, UINT** `nPos` **);**|
|**ON_WM_PARENTNOTIFY_REFLECT( )**|**afx_msg void ParentNotify ( UINT** `message` **, LPARAM** `lParam` **);**|

ON_NOTIFY_REFLECT 和 ON_CONTROL_REFLECT 宏所具有的变体，它允许多个对象 （如控件和其父级） 来处理给定的消息。

|映射条目|函数原型|
|---------------|------------------------|
|**ON_NOTIFY_REFLECT_EX(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **( NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT**<strong>\*</strong> *result* **);**|
|**ON_CONTROL_REFLECT_EX(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **( );**|

## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>处理反射消息：可重用控件的示例

这个简单的示例创建名为的可重用控件`CYellowEdit`。 控件的工作方式相同常规编辑控件，只不过它将黄色背景上显示黑色文本。 它可以很容易地添加将允许的成员函数`CYellowEdit`控件来显示不同的颜色。

### <a name="to-try-the-example-that-creates-a-reusable-control"></a>若要尝试创建可重用控件的示例

1. 在现有应用程序中创建一个新对话框。 有关详细信息，请参阅[对话框编辑器](../windows/dialog-editor.md)主题。

   必须具有用来开发可重用控件的应用程序。 如果没有现有的应用程序使用，创建一个基于对话框的应用程序，使用应用程序向导。

2. 与你的项目加载到 Visual C++，使用类向导创建一个名为的新类`CYellowEdit`基于`CEdit`。

3. 三个成员将变量添加到你`CYellowEdit`类。 将前两个*COLORREF*变量以保存的文本颜色和背景色。 第三个将`CBrush`对象将包含对于绘制背景的画笔。 `CBrush`对象允许你创建一次，只是对其进行引用之后，画笔，时自动销毁画笔`CYellowEdit`销毁控件。

4. 通过按如下所示编写构造函数中初始化成员变量：

    ```cpp
    CYellowEdit::CYellowEdit()
    {
        m_clrText = RGB(0, 0, 0);
        m_clrBkgnd = RGB(255, 255, 0);
        m_brBkgnd.CreateSolidBrush(m_clrBkgnd);
    }
    ```

5. 使用类向导，将添加到反射 WM_CTLCOLOR 消息的处理程序在`CYellowEdit`类。 请注意，可以处理的消息的列表中的消息名称的前面在等号指示反映该消息。 这中所述[为反射消息定义消息处理程序](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)。

   类向导为您添加下面的消息映射宏和主干函数：

    ```cpp
    ON_WM_CTLCOLOR_REFLECT()
    // Note: other code will be in between....

    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)
    {
        // TODO: Change any attributes of the DC here
        // TODO: Return a non-NULL brush if the
        //       parent's handler should not be called
        return NULL;
    }
    ```

6. 将以下代码替换为函数的主体。 该代码指定的文本颜色、 文本背景色和其余控件的背景色。

    ```cpp
    pDC->SetTextColor(m_clrText);   // text
    pDC->SetBkColor(m_clrBkgnd);    // text bkgnd
    return m_brBkgnd;               // ctl bkgnd
    ```

7. 在对话框中，创建一个编辑控件，然后通过按住 control 密钥下的同时双击编辑控件将其附加到成员变量。 在添加成员变量对话框中，完成变量的名称并选择"控件"类别，然后"CYellowEdit"的变量的类型。 别忘了在对话框中设置 tab 键顺序。 此外，请确保包含标头文件`CYellowEdit`对话框的标头文件中的控件。

8. 生成并运行应用程序。 编辑控件将具有黄色背景。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
