---
title: "处理自定义通知 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TBN_CUSTHELP
- TBN_QUERYINSERT
- TBNOTIFY
- NMHDR
- TBN_TOOLBARCHANGE
- TBN_ENDDRAG
- NM_SETFOCUS
- TBN_RESET
- NM_RETURN
- NM_ENDWAIT
- NM_STARTWAIT
- TBN_BEGINDRAG
- NM_OUTOFMEMORY
- TBN_QUERYDELETE
- NM_DBLCLK
- TBN_ENDADJUST
- NM_KILLFOCUS
- NM_RCLICK
- TBN_BEGINADJUST
- NM_CLICK
dev_langs: C++
helpviewer_keywords:
- TBN_ENDADJUST notification [MFC]
- TBNOTIFY notification [MFC]
- TBN_BEGINDRAG notification [MFC]
- TBN_TOOLBARCHANGE notification [MFC]
- NM_CLICK notification [MFC]
- NM_RETURN notification [MFC]
- NM_RCLICK notification [MFC]
- TBN_ENDDRAG notification [MFC]
- TBN_BEGINADJUST notification [MFC]
- NM_ENDWAIT notification [MFC]
- NM_KILLFOCUS notification [MFC]
- NM_SETFOCUS notification [MFC]
- NM_OUTOFMEMORY notification [MFC]
- TBN_QUERYINSERT notification [MFC]
- NMHDR [MFC]
- NM_STARTWAIT notification [MFC]
- CToolBarCtrl class [MFC], handling notifications
- TBN_CUSTHELP notification [MFC]
- TBN_RESET notification [MFC]
- NM_DBLCLK notification [MFC]
- TBN_QUERYDELETE notification [MFC]
- NM_RDBLCLK notification [MFC]
- TBN_GETBUTTONINFO notification [MFC]
ms.assetid: 219ea08e-7515-4b98-85cb-47120f08c0a2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ec4561fda34ba2b20f7fe46aea52f272eed3b9ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="handling-customization-notifications"></a>处理自定义通知
Windows 工具栏公共控件有内置的自定义功能，包括一个系统定义的自定义对话框，使用户可以插入、删除或重排工具栏按钮。 应用程序确定自定义功能是否可用，并控制用户可以自定义工具栏的程度。  
  
 你可以通过赋予工具栏 `CCS_ADJUSTABLE` 样式，使这些自定义功能对用户可用。 用户可以通过自定义功能将按钮拖动到新位置，或通过将按钮拖出工具栏删除该按钮。 此外，用户可以双击工具栏以显示  “自定义工具栏”对话框，以便添加、删除和重排工具栏按钮。 应用程序通过使用 [Customize](../mfc/reference/ctoolbarctrl-class.md#customize) 成员函数来显示对话框。  
  
 工具控件在自定义过程的每一步都会向父窗口发送通知消息。 如果用户按住 SHIFT 键并开始拖动按钮，工具栏将自动处理拖动操作。 工具栏将向父窗口发送 **TBN_QUERYDELETE** 通知消息，确定是否可删除该按钮。 如果父窗口返回 **FALSE**，则结束拖动操作。 否则，工具栏将捕获鼠标输入并等待用户释放鼠标按钮。  
  
 当用户释放鼠标按钮时，工具栏控件将确定鼠标光标的位置。 如果光标位于工具栏之外，将删除该按钮。 如果光标位于另一个工具栏按钮上，工具栏将向父窗口发送 **TBN_QUERYINSERT** 通知消息，以确定是否可以将按钮插入到给定按钮的左侧。 如果父窗口返回 **TRUE**，则将插入该按钮；否则将不会插入。 工具栏将发送 **TBN_TOOLBARCHANGE** 通知消息，表示拖动操作结束。  
  
 如果用户没有按住 SHIFT 键就开始拖动操作，工具栏控件将向所有者窗口发送 **TBN_BEGINDRAG** 通知消息。 实现了自己的按钮拖动代码的应用程序可以将此消息用作开始拖动操作的信号。 工具栏将发送 **TBN_ENDDRAG** 通知消息，表示拖动操作结束。  
  
 工具栏控件在用户通过使用  “自定义工具栏”对话框自定义工具栏时，将发送通知消息。 工具栏将在用户双击工具栏之后，在创建对话框之前发送 **TBN_BEGINADJUST** 。 然后，工具栏开始发送一系列 **TBN_QUERYINSERT** 通知消息，以确定工具栏是否允许插入按钮。 当父窗口返回 **TRUE**时，工具栏将停止发送 **TBN_QUERYINSERT** 通知消息。 如果父窗口对于任何按钮未返回 **TRUE** ，工具栏将销毁对话框。  
  
 然后，工具栏控件将确定通过对工具栏上的每个按钮发送 **TBN_QUERYDELETE** 通知消息，确定是否可从工具栏中删除任何按钮。 父窗口返回 **TRUE** ，表示可以删除某个按钮；返回 **FALSE**，表示不可以删除。 工具栏将所有的工具栏按钮都添加到对话框，但用灰色表示不可删除的按钮。  
  
 每当工具栏控件需要自定义工具栏对话框中某个按钮的信息时，它都会发送 **TBN_GETBUTTONINFO** 通知消息，用于指定需要其信息的按钮的索引和 **TBNOTIFY** 结构的地址。 父窗口必须使用相关信息填充该结构。  
  
  “自定义工具栏”对话框包括“帮助”按钮和“重置”按钮。 当用户选择“帮助”按钮时，工具栏控件将发送 **TBN_CUSTHELP** 通知消息。 父窗口应通过显示帮助信息进行响应。 当用户选择“重置”按钮时，对话框中将发送 **TBN_RESET** 通知消息。 此消息表示工具栏将重新初始化对话框。  
  
 这些消息都是 **WM_NOTIFY** 消息。将下列形式的消息映射项添加到所有者窗口消息映射中，就可以在所有者窗口中处理这些消息：  
  
 `ON_NOTIFY( wNotifyCode, idControl, memberFxn )`  
  
 `wNotifyCode`  
 通知消息标识符代码，如 **TBN_BEGINADJUST**。  
  
 `idControl`  
 发送通知的控件的标识符。  
  
 `memberFxn`  
 接收到通知时调用的成员函数。  
  
 成员函数将用下列原型声明：  
  
 `afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );`  
  
 如果消息通知处理程序返回一个值，它应将其放入由 **result** 指向的 *LRESULT*中。  
  
 对于每一条消息， `pNotifyStruct` 不是指向 **NMHDR** 结构，就是指向 **TBNOTIFY** 结构。 这些结构如下所述：  
  
 **NMHDR** 结构包含以下成员：  
  
 `typedef struct tagNMHDR {`  
  
 `HWND hwndFrom;  // handle of control sending message`  
  
 `UINT idFrom;// identifier of control sending message`  
  
 `UINT code;  // notification code; see below`  
  
 `} NMHDR;`  
  
 **hwndFrom**  
 发送通知的控件的窗口句柄。 要将此句柄转换为 `CWnd` 指针，可使用 [CWnd::FromHandle](../mfc/reference/cwnd-class.md#fromhandle)。  
  
 **idFrom**  
 发送通知的控件的标识符。  
  
 **代码**  
 通知代码： 此成员可以是特定于控件类型的值，如 **TBN_BEGINADJUST** 或 **TTN_NEEDTEXT**，或者是下面列出的常见通知值之一：  
  
-   **NM_CLICK** 用户已在控件内单击了鼠标左键。  
  
-   **NM_DBLCLK** 用户已在控件内双击了鼠标左键。  
  
-   **NM_KILLFOCUS** 控件已丢失输入焦点。  
  
-   **NM_OUTOFMEMORY** 控件无法完成操作，因为没有足够的内存可用。  
  
-   **NM_RCLICK** 用户已在控件内单击了鼠标右键。  
  
-   **NM_RDBLCLK** 用户已在控件内双击了鼠标右键。  
  
-   **NM_RETURN** 控件具有输入焦点并且用户已按了 ENTER 键。  
  
-   **NM_SETFOCUS** 控件已收到输入焦点。  
  
 **TBNOTIFY** 结构包含以下成员：  
  
 `typedef struct {`  
  
 `NMHDR hdr; // information common to all WM_NOTIFY messages`  
  
 `int iItem; // index of button associated with notification`  
  
 `TBBUTTON tbButton; // info about button associated withnotification`  
  
 `int cchText;   // count of characters in button text`  
  
 `LPSTR lpszText;// address of button text`  
  
 `} TBNOTIFY, FAR* LPTBNOTIFY;`  
  
## <a name="remarks"></a>备注  
 **hdr**  
 所有 **WM_NOTIFY** 消息的公用消息。  
  
 **iItem**  
 与通知关联的按钮索引。  
  
 **tbButton**  
 `TBBUTTON`结构，它包含与通知关联的工具栏按钮有关的信息。  
  
 **cchText**  
 按钮文本中的字符数。  
  
 **lpszText**  
 指向按钮文本的指针。  
  
 工具栏发送的通知如下所示：  
  
-   **TBN_BEGINADJUST** 当用户开始自定义工具栏控件时发送 指针指向包含有关通知的信息的 **NMHDR** 结构。 处理程序不需要返回任何特定值。  
  
-   **TBN_BEGINDRAG** 当用户开始在工具栏中拖动按钮时发送。 指针指向 **TBNOTIFY** 结构。 **iItem** 成员包含正在拖动的按钮的从零开始的索引。 处理程序不需要返回任何特定值。  
  
-   **TBN_CUSTHELP** 当用户在“自定义工具栏”对话框中选择“帮助”按钮时发送。 没有返回值。 指针指向包含有关通知消息的信息的 **NMHDR** 结构。 处理程序不需要返回任何特定值。  
  
-   **TBN_ENDADJUST** 当用户停止自定义工具栏控件时发送。 指针指向包含有关通知消息的信息的 **NMHDR** 结构。 处理程序不需要返回任何特定值。  
  
-   **TBN_ENDDRAG** 当用户停止在工具栏控件中拖动按钮时发送。 指针指向 **TBNOTIFY** 结构。 **iItem** 成员包含正在拖动的按钮的从零开始的索引。 处理程序不需要返回任何特定值。  
  
-   **TBN_GETBUTTONINFO** 当用户正在自定义工具栏控件时发送。 工具栏使用此通知消息来检索自定义工具栏对话框所需的信息。 指针指向 **TBNOTIFY** 结构。 **iItem** 成员指定按钮的从零开始的索引。 **pszText** 和 **cchText** 成员指定当前按钮文本的地址和长度（以字符为单位）。 应用程序应使用有关按钮的信息填充结构。 如果已将按钮信息复制到结构，则返回 **TRUE** ，否则返回 **FALSE** 。  
  
-   **TBN_QUERYDELETE** 当用户正在自定义工具栏控件时发送，以确定是否可以从工具栏控件中删除某个按钮。 指针指向 **TBNOTIFY** 结构。 **iItem** 成员包含要删除的按钮的从零开始的索引。 返回 **TRUE** ，允许删除该按钮，或返回 **FALSE** ，阻止删除该按钮。  
  
-   **TBN_QUERYINSERT** 当用户正在自定义工具栏控件时发送，以确定是否可以将某一按钮插入到给定按钮的左侧。 指针指向 **TBNOTIFY** 结构。 **iItem** 成员包含要插入的按钮的从零开始的索引。 返回 **TRUE** ，允许将按钮插入到给定按钮之前，或返回 **FALSE** ，阻止插入按钮。  
  
-   **TBN_RESET** 当用户重置“自定义工具栏”对话框的内容时发送。 指针指向包含有关通知消息的信息的 **NMHDR** 结构。 处理程序不需要返回任何特定值。  
  
-   **TBN_TOOLBARCHANGE** 用户已自定义工具栏控件后发送。 指针指向包含有关通知消息的信息的 **NMHDR** 结构。 处理程序不需要返回任何特定值。  
  
## <a name="see-also"></a>请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

