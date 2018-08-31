---
title: TN061： 和 WM_NOTIFY 消息 |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
dev_langs:
- C++
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d2f1259227fa8d27778dbf0e40b13f5460b7041
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218780"
---
# <a name="tn061-onnotify-and-wmnotify-messages"></a>TN061：ON_NOTIFY 和 WM_NOTIFY 消息

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

此技术说明提供有关新的 WM_NOTIFY 消息的背景信息，并介绍处理 WM_NOTIFY 消息在 MFC 应用程序中的建议 （也是最常见） 的方法。

**Windows 中的通知消息 3.x**

在 Windows 3.x 中，通过将一条消息发送到父控件通知的事件，例如鼠标单击其父级更改内容和所选内容，以及控件背景的绘制。 简单的通知作为特殊 WM_COMMAND 消息通知代码 （如 BN_CLICKED) 发送，并且控制 ID 打包到*wParam*和中的控件的句柄*lParam*。 请注意，由于*wParam*并*lParam*是否完整，没有方法传递任何其他数据，这些消息可以是简单的通知。 例如，在 BN_CLICKED 通知中，没有发送有关鼠标光标的位置的信息，当单击此按钮的任何方法。

当控件在 Windows 3.x 需要发送通知消息，其中包含其他数据时，它们使用不同的专用的消息，包括 WM_CTLCOLOR、 WM_VSCROLL、 WM_HSCROLL、 WM_DRAWITEM、 WM_MEASUREITEM、 WM_COMPAREITEM、 WM_DELETEITEM、 WM_CHARTOITEM、 WM_VKEYTOITEM，等等。 这些消息可以反映给向他们发送的控件。 有关详细信息，请参阅[TN062: Windows 控件消息反射](../mfc/tn062-message-reflection-for-windows-controls.md)。

**Win32 中的通知消息**

对于在 Windows 3.1 中已存在的控件，Win32 API 使用的大部分使用了通知消息在 Windows 3.x。 但是，Win32 还添加了一些复杂的复杂控件所支持在 Windows 3.x。 通常情况下，这些控件需要发送包含其通知消息的额外数据。 而不是添加一个新**WM_** <strong>\*</strong>消息的每个新通知所需的其他数据，Win32 API 的设计器选择添加只是一条消息，WM_NOTIFY，可以传递任何以标准化的方式的其他数据量。

WM_NOTIFY 消息包含发送消息的控件的 ID *wParam*和指向一个结构中的*lParam*。 此结构是**NMHDR**结构或具有某种可查看大结构**NMHDR**结构作为其第一个成员。 请注意，由于**NMHDR**成员为第一个，可作为任一的指针到指向此结构的指针**NMHDR**或作为更大的结构，具体取决于如何把它强制转换到的指针。

在大多数情况下，指针将指向更大的结构，你将需要使用它时将其强制转换。 在少量的通知，例如常见的通知 (其名称开头**NM_**) 和工具提示控件的 TTN_SHOW 和 TTN_POP 通知，是**NMHDR**实际使用的结构。

**NMHDR**结构或初始成员包含的句柄和发送消息和通知代码 （如 TTN_SHOW) 的控件的 ID。 格式**NMHDR**结构如下所示：

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

对于 TTN_SHOW 消息，**代码**成员将设置为 TTN_SHOW。

大多数通知将指针传递到更大的结构，其中包含**NMHDR**结构作为其第一个成员。 例如，请考虑使用列表视图控件的 LVN_KEYDOWN 通知消息，该列表视图控件中按下某个键时，将发送的结构。 指针指向**LV_KEYDOWN**结构，如下所示定义：

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

请注意，由于**NMHDR**成员是此结构中的第一行中，通知消息中传递的指针可以转换为指针**NMHDR**或指向的**LV_KEYDOWN**.

**对所有新的 Windows 控件通用的通知**

某些通知是普遍适用于所有新的 Windows 控件。 这些通知将传递一个指向**NMHDR**结构。

|通知代码|由于发送|
|-----------------------|------------------|
|NM_CLICK|用户单击鼠标按钮在控件中|
|NM_DBLCLK|在控件中的用户双击的鼠标左键|
|NM_RCLICK|用户单击鼠标右键按钮在控件中|
|NM_RDBLCLK|用户双击的鼠标右键按钮在控件中|
|NM_RETURN|用户按下 ENTER 键时控件具有输入焦点|
|NM_SETFOCUS|控件没有获得输入的焦点|
|NM_KILLFOCUS|控件已丢失输入的焦点|
|NM_OUTOFMEMORY|控件无法完成操作，因为没有足够的内存|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> ON_NOTIFY： 处理在 MFC 应用程序中的 WM_NOTIFY 消息

该函数`CWnd::OnNotify`处理通知消息。 其默认实现将检查通知处理程序调用的消息映射。 一般情况下，您不会重写`OnNotify`。 相反，提供处理程序函数，并将该处理程序的消息映射项添加到所有者窗口的类的消息映射。

类向导，通过 ClassWizard 属性页中，可以创建 ON_NOTIFY 消息映射条目和主干处理程序函数为您提供。 有关使用类向导来简化此过程的详细信息，请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。

ON_NOTIFY 消息映射宏具有以下语法：

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

参数的位置是：

*wNotifyCode*  
 通知消息来处理，例如 LVN_KEYDOWN 的代码。

*id*  
 为其发送通知的控件子标识符。

*memberFxn*  
 要发送此通知时调用的成员函数。

必须使用以下原型声明成员函数：

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

参数的位置是：

*pNotifyStruct*  
 指向通知结构，如上面的部分中所述的指针。

*结果*  
 您将设置指向结果代码的步骤，再返回。

## <a name="example"></a>示例

以指定你希望此成员函数`OnKeydownList1`来处理来自 LVN_KEYDOWN 消息`CListCtrl`其 ID 是`IDC_LIST1`，将使用类向导将以下内容添加到消息映射：

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

在上述示例中，提供的 ClassWizard 函数是：

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;
    
    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

请注意 ClassWizard 自动提供正确的类型的指针。 可以通过访问通知结构*pNMHDR*或*pLVKeyDow*。

##  <a name="_mfcnotes_on_notify_range"></a> ON_NOTIFY_RANGE

如果你需要处理同一 WM_NOTIFY 消息的一组控件，可以使用 ON_NOTIFY_RANGE 而不是 ON_NOTIFY。 例如，可能有一组你想要为某些通知消息执行相同操作的按钮。

ON_NOTIFY_RANGE 使用时，指定要为其通过指定开始和结束范围的子标识符来处理通知消息的子标识符的连续范围。

ClassWizard 不会处理 ON_NOTIFY_RANGE;若要使用它，您需要编辑消息映射自己的帐户。

消息映射条目和 ON_NOTIFY_RANGE 函数原型如下所示：

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

参数的位置是：

*wNotifyCode*  
 通知消息来处理，例如 LVN_KEYDOWN 的代码。

*id*  
 在连续范围的标识符中第一个标识符。

*idLast*  
 在连续范围的标识符中的最后一个标识符。

*memberFxn*  
 要发送此通知时调用的成员函数。

必须使用以下原型声明成员函数：

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

参数的位置是：

*id*  
 向你发送通知的控件子标识符。

*pNotifyStruct*  
 指向通知结构，如上文所述的指针。

*结果*  
 您将设置指向结果代码的步骤，再返回。

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON_NOTIFY_EX ON_NOTIFY_EX_RANGE

如果你想路由以处理一条消息通知中的多个对象，可以使用 ON_NOTIFY_EX （或 ON_NOTIFY_EX_RANGE），而不是 ON_NOTIFY （或 ON_NOTIFY_RANGE）。 之间的唯一区别**EX**版本和正式版本是用于调用的成员函数**EX**版本返回**BOOL** ，该值指示是否消息处理应继续。 返回**FALSE**从此函数使你可以处理同一消息中多个对象。

ClassWizard 不处理 ON_NOTIFY_EX 或 ON_NOTIFY_EX_RANGE;如果你想要使用其中任何一个，您需要编辑消息映射自己的帐户。

消息映射条目和 ON_NOTIFY_EX 和 ON_NOTIFY_EX_RANGE 函数原型如下所示。 参数的含义是相同的非**EX**版本。

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

这两个以上的原型是相同的：

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

在这两种情况下， *id*保存通知发送给该控件的子标识符。

你的函数必须返回 **，则返回 TRUE**如果已完全处理通知消息或**FALSE**命令路由中的其他对象应具有处理消息的机会。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)  
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)  
