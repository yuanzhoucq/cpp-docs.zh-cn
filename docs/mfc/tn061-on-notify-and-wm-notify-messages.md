---
title: TN061：ON_NOTIFY 和 WM_NOTIFY 消息
ms.date: 06/28/2018
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
ms.openlocfilehash: 845558dad6b9f6e820c759cb83fce2c6cbceaa0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366600"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061：ON_NOTIFY 和 WM_NOTIFY 消息

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本技术说明提供有关新WM_NOTIFY消息的背景信息，并描述了在 MFC 应用程序中处理WM_NOTIFY消息的建议（也是最常见的）方法。

**Windows 3.x 中的通知消息**

在 Windows 3.x 中，控件通过向父级发送消息来通知其父级有关诸如鼠标单击、内容和选择更改以及控制背景绘制等事件。 简单的通知作为特殊WM_COMMAND消息发送，通知代码（如BN_CLICKED）和控制 ID 打包到*wParam*中，控件的句柄在*lParam*中。 请注意，由于*wParam*和*lParam*已满，因此无法传递任何其他数据 - 这些消息只能是简单的通知。 例如，在BN_CLICKED通知中，无法发送有关单击按钮时鼠标光标位置的信息。

当 Windows 3.x 中的控件需要发送包含其他数据的通知消息时，它们使用各种特殊用途的消息，包括WM_CTLCOLOR、WM_VSCROLL、WM_HSCROLL、WM_DRAWITEM、WM_MEASUREITEM、WM_COMPAREITEM、WM_DELETEITEM、WM_CHARTOITEM、WM_VKEYTOITEM等。 这些消息可以反射回发送它们的控件。 有关详细信息，请参阅[TN062：Windows 控件的消息反射](../mfc/tn062-message-reflection-for-windows-controls.md)。

**Win32 中的通知消息**

对于 Windows 3.1 中存在的控件，Win32 API 使用 Windows 3.x 中使用的大多数通知消息。 但是，Win32 还会向 Windows 3.x 中支持的控件添加许多复杂、复杂的控件。 通常，这些控件需要发送其他数据及其通知消息。 Win32 API 的设计者选择只添加一条消息，即WM_NOTIFY，该消息可以以标准化的方式传递任意数量的附加数据，而不是为每个需要额外数据的新通知添加新**WM_**<strong>\*</strong>消息。

WM_NOTIFY消息包含在*wParam*中发送消息的控件的 ID 和指向*lParam*中结构的指针。 此结构要么是**NMHDR**结构，要么是具有**NMHDR**结构作为其第一个成员的较大结构。 请注意，由于**NMHDR**成员是第一个，因此指向此结构的指针可用作指向**NMHDR**的指针或指向较大结构的指针，具体取决于您如何施放它。

在大多数情况下，指针将指向较大的结构，并且在使用它时需要强制转换它。 在少数通知中，例如常见通知（其名称以**NM_** 开头）和工具提示控件的TTN_SHOW和TTN_POP通知）实际上是实际使用的**NMHDR**结构。

**NMHDR**结构或初始成员包含发送消息的控件的句柄和 ID 以及通知代码（如TTN_SHOW）。 **NMHDR**结构的格式如下所示：

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

对于TTN_SHOW消息，**代码**成员将设置为TTN_SHOW。

大多数通知传递指向包含**NMHDR**结构作为其第一个成员的较大结构的指针。 例如，请考虑列表视图控件LVN_KEYDOWN通知消息所使用的结构，该结构在列表视图控件中按下键时发送。 指针指向**LV_KEYDOWN**结构，该结构的定义如下所示：

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

请注意，由于**NMHDR**成员是此结构中的第一个，因此在通知消息中传递的指针可以转换为指向**NMHDR**的指针或指向**LV_KEYDOWN**的指针。

**所有新窗口控件共有的通知**

某些通知是所有新的 Windows 控件所共有的。 这些通知传递指向**NMHDR**结构的指针。

|通知代码|发送是因为|
|-----------------------|------------------|
|NM_CLICK|用户单击控件中的左鼠标按钮|
|NM_DBLCLK|控件中用户双击左鼠标按钮|
|NM_RCLICK|用户单击控件中的鼠标右键|
|NM_RDBLCLK|控件中的用户双击右鼠标按钮|
|NM_RETURN|用户按下 ENTER 键，而控件具有输入焦点|
|NM_SETFOCUS|已给予控件输入焦点|
|NM_KILLFOCUS|控制已丢失输入焦点|
|NM_OUTOFMEMORY|控件无法完成操作，因为内存不足|

## <a name="on_notify-handling-wm_notify-messages-in-mfc-applications"></a><a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY：在 MFC 应用程序中处理WM_NOTIFY消息

该函数`CWnd::OnNotify`处理通知消息。 其默认实现检查消息映射，以便通知处理程序调用。 通常，您不重写`OnNotify`。 相反，您提供一个处理程序函数，并将该处理程序的消息映射条目添加到所有者窗口类的消息映射中。

ClassWizard 通过 ClassWizard 属性表可以创建ON_NOTIFY消息映射条目，并为您提供骨架处理程序函数。 有关使用 ClassWizard 使其更容易的详细信息，请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。

ON_NOTIFY消息映射宏具有以下语法：

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

参数的位置是：

*wNotifyCode*<br/>
要处理的通知消息的代码，如LVN_KEYDOWN。

*id*<br/>
发送通知的控件的子标识符。

*成员Fxn*<br/>
发送此通知时要调用的成员函数。

成员函数必须使用以下原型声明：

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

参数的位置是：

*通知*<br/>
指向通知结构的指针，如上一节所述。

*结果*<br/>
返回前要设置的结果代码的指针。

## <a name="example"></a>示例

要指定成员函数`OnKeydownList1`处理来自`CListCtrl`其 ID 的消息`IDC_LIST1`LVN_KEYDOWN，请使用 ClassWizard 将以下内容添加到消息映射中：

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

在上面的示例中，ClassWizard 提供的函数是：

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

请注意，ClassWizard 会自动提供正确类型的指针。 您可以通过*pNMHDR*或*pLVKeyDow*访问通知结构。

## <a name="on_notify_range"></a><a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

如果需要为一组控件处理相同的WM_NOTIFY消息，则可以使用ON_NOTIFY_RANGE而不是ON_NOTIFY。 例如，您可能有一组按钮，您希望对特定通知消息执行相同的操作。

使用ON_NOTIFY_RANGE时，您可以指定一个连续的子标识符范围，通过指定范围的开头和结尾子标识符来处理通知消息。

类向导不处理ON_NOTIFY_RANGE;要使用它，您需要自己编辑邮件映射。

ON_NOTIFY_RANGE的消息映射条目和函数原型如下所示：

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

参数的位置是：

*wNotifyCode*<br/>
要处理的通知消息的代码，如LVN_KEYDOWN。

*id*<br/>
连续标识符范围内的第一个标识符。

*idLast*<br/>
连续标识符范围中的最后一个标识符。

*成员Fxn*<br/>
发送此通知时要调用的成员函数。

成员函数必须使用以下原型声明：

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

参数的位置是：

*id*<br/>
发送通知的控件的子标识符。

*通知*<br/>
如上所述，指向通知结构的指针。

*结果*<br/>
返回前要设置的结果代码的指针。

## <a name="on_notify_ex-on_notify_ex_range"></a><a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX，ON_NOTIFY_EX_RANGE

如果希望通知路由中有多个对象来处理消息，则可以使用ON_NOTIFY_EX（或ON_NOTIFY_EX_RANGE），而不是ON_NOTIFY（或ON_NOTIFY_RANGE）。 **EX**版本和常规版本的唯一区别是，EX**版本调用**的成员函数返回**BOOL，** 指示消息处理是否应继续。 通过从此函数返回**FALSE，** 您可以在多个对象中处理同一消息。

ClassWizard 不处理ON_NOTIFY_EX或ON_NOTIFY_EX_RANGE;如果要使用其中任一，则需要自己编辑邮件映射。

ON_NOTIFY_EX和ON_NOTIFY_EX_RANGE的消息映射条目和函数原型如下。 参数的含义与非**EX**版本的含义相同。

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

上述两个原型都相同：

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

在这两种情况下 *，id*都保存发送通知的控件的子标识符。

如果通知消息已完全处理，则函数必须返回**TRUE;** 如果命令路由中的其他对象应有机会处理该消息，则函数必须返回**TRUE。**

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
