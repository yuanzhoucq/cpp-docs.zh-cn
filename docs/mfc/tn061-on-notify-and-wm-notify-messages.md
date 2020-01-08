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
ms.openlocfilehash: aa1efb628ee45be3dfaee320cf64c4b2cbb91f04
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302232"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061：ON_NOTIFY 和 WM_NOTIFY 消息

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本技术说明提供了有关新 WM_NOTIFY 消息的背景信息，并介绍了在 MFC 应用程序中处理 WM_NOTIFY 消息的建议（以及最常见的方法）。

**Windows 3.x 中的通知消息**

在 Windows 3.x 中，控件会通知其父事件，如鼠标单击、内容中的更改和选择，以及通过将消息发送到父项来控制背景绘制。 简单通知以特殊 WM_COMMAND 消息形式发送，通知代码（如 BN_CLICKED）和控件 ID 打包到*wParam*和*lParam*中的控件句柄。 请注意，由于*wParam*和*lParam*已满，因此无法传递任何其他数据，这些消息只是简单通知。 例如，在 BN_CLICKED 通知中，单击按钮时，无法发送有关鼠标光标位置的信息。

当 Windows 3.x 中的控件需要发送包含其他数据的通知消息时，它们使用各种特殊用途的消息，包括 WM_CTLCOLOR、WM_VSCROLL、WM_HSCROLL、WM_DRAWITEM、WM_MEASUREITEM、WM_COMPAREITEM、WM_DELETEITEM、WM_CHARTOITEM、WM_VKEYTOITEM 等。 这些消息可以反映回发送的控件。 有关详细信息，请参阅[TN062： Windows 控件的消息反射](../mfc/tn062-message-reflection-for-windows-controls.md)。

**Win32 中的通知消息**

对于 Windows 3.1 中存在的控件，Win32 API 使用在 Windows 3.x 中使用的大多数通知消息。 但是，Win32 还会将大量复杂的复杂控件添加到 Windows 2.x 支持的控件中。 通常，这些控件需要连同通知消息一起发送额外的数据。 Win32 API 的设计器选择只添加一条消息，而不是为需要额外数据的每个新通知添加新的**WM_** <strong>\*</strong>消息，而是选择只添加一条消息 WM_NOTIFY，该消息可以采用标准化方式传递任意数量的附加数据。

WM_NOTIFY 消息包含在*wParam*中发送消息的控件的 ID 以及指向*lParam*中的结构的指针。 此结构可以是**NMHDR**结构，也可以是将**NMHDR**结构作为其第一个成员的更大结构。 请注意，由于**NMHDR**成员是第一个，因此指向此结构的指针可用作指向**NMHDR**的指针，或用作指向更大结构的指针（具体取决于您如何强制转换）。

在大多数情况下，指针将指向更大的结构，并且在使用时需要进行转换。 只有几个通知，如常见通知（其名称以**NM_** 开头）和工具提示控件的 TTN_SHOW 和 TTN_POP 通知，都是实际使用的**NMHDR**结构。

**NMHDR**结构或初始成员包含发送消息的控件的句柄和 ID 以及通知代码（如 TTN_SHOW）。 **NMHDR**结构的格式如下所示：

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

对于 TTN_SHOW 消息，**代码**成员将设置为 TTN_SHOW。

大多数通知会将一个指针传递到一个更大的结构，该结构包含**NMHDR**结构作为其第一个成员。 例如，请考虑列表视图控件的 LVN_KEYDOWN 通知消息所使用的结构，在列表视图控件中按下某个键时将发送该消息。 指针指向**LV_KEYDOWN**结构，如下所示：

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

请注意，因为**NMHDR**成员是此结构中的第一个成员，所以在通知消息中传递的指针可以转换为指向**NMHDR**的指针或指向**LV_KEYDOWN**的指针。

**所有新 Windows 控件通用的通知**

某些通知对于所有新的 Windows 控件都很常见。 这些通知传递指向**NMHDR**结构的指针。

|通知代码|发送原因|
|-----------------------|------------------|
|NM_CLICK|用户在控件中单击了鼠标左键|
|NM_DBLCLK|用户在控件中双击了鼠标左键|
|NM_RCLICK|用户在控件中单击了鼠标右键|
|NM_RDBLCLK|用户在控件中双击了鼠标右键|
|NM_RETURN|用户按下 ENTER 键时控件具有输入焦点|
|NM_SETFOCUS|控件已获得输入焦点|
|NM_KILLFOCUS|控件已丢失输入焦点|
|NM_OUTOFMEMORY|由于没有足够的可用内存，控件无法完成操作|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY：在 MFC 应用程序中处理 WM_NOTIFY 消息

函数 `CWnd::OnNotify` 处理通知消息。 其默认实现将检查消息映射，以使通知处理程序可以调用。 通常，不会重写 `OnNotify`。 而是提供处理函数，并将该处理程序的消息映射项添加到所有者窗口类的消息映射中。

ClassWizard 通过 ClassWizard 属性表，可以创建 ON_NOTIFY 消息映射项，并为用户提供主干处理程序函数。 若要详细了解如何使用 ClassWizard 来简化此过程，请参阅将[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。

ON_NOTIFY 消息映射宏具有以下语法：

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

参数的位置是：

*wNotifyCode*<br/>
要处理的通知消息的代码，如 LVN_KEYDOWN。

*id*<br/>
要向其发送通知的控件的子标识符。

*memberFxn*<br/>
发送此通知时要调用的成员函数。

必须用以下原型声明成员函数：

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

参数的位置是：

*pNotifyStruct*<br/>
指向通知结构的指针，如以上部分所述。

result<br/>
指向在返回之前要设置的结果代码的指针。

## <a name="example"></a>示例

若要指定成员函数 `OnKeydownList1` 处理来自其 ID `IDC_LIST1`的 `CListCtrl` LVN_KEYDOWN 消息，可以使用 ClassWizard 将以下内容添加到消息映射：

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

请注意，ClassWizard 会自动提供适当类型的指针。 可以通过*pNMHDR*或*pLVKeyDow*访问通知结构。

##  <a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

如果需要为一组控件处理相同的 WM_NOTIFY 消息，则可以使用 ON_NOTIFY_RANGE 而不是 ON_NOTIFY。 例如，你可能有一组按钮，你希望为某个通知消息执行相同的操作。

使用 ON_NOTIFY_RANGE 时，可以通过指定范围的开始和结束子标识符来指定要处理通知消息的子标识符的连续范围。

ClassWizard 未处理 ON_NOTIFY_RANGE;若要使用它，需要自行编辑消息映射。

ON_NOTIFY_RANGE 的消息映射项和函数原型如下所示：

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

参数的位置是：

*wNotifyCode*<br/>
要处理的通知消息的代码，如 LVN_KEYDOWN。

*id*<br/>
标识符的连续范围中的第一个标识符。

*idLast*<br/>
标识符连续范围中的最后一个标识符。

*memberFxn*<br/>
发送此通知时要调用的成员函数。

必须用以下原型声明成员函数：

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

参数的位置是：

*id*<br/>
发送通知的控件的子标识符。

*pNotifyStruct*<br/>
指向通知结构的指针，如上所述。

result<br/>
指向在返回之前要设置的结果代码的指针。

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX，ON_NOTIFY_EX_RANGE

如果希望通知路由中有多个对象处理消息，则可以使用 ON_NOTIFY_EX （或 ON_NOTIFY_EX_RANGE）而不是 ON_NOTIFY （或 ON_NOTIFY_RANGE）。 **Ex**版本和常规版本之间唯一的区别是，针对**ex**版本调用的成员函数返回一个**布尔**值，指示消息处理是否应继续。 通过从此函数返回**FALSE** ，可以在多个对象中处理同一消息。

ClassWizard 不处理 ON_NOTIFY_EX 或 ON_NOTIFY_EX_RANGE;如果要使用其中任一方法，则需要自行编辑消息映射。

ON_NOTIFY_EX 和 ON_NOTIFY_EX_RANGE 的消息映射项和函数原型如下所示。 参数的含义与非**EX**版本的含义相同。

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

上述两个的原型是相同的：

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

在这两种情况下， *id*都包含发送通知的控件的子标识符。

如果通知消息已完全处理，则函数必须返回**TRUE** ; 如果命令路由中的其他对象应该有机会处理消息，则必须返回**FALSE** 。

## <a name="see-also"></a>另请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
