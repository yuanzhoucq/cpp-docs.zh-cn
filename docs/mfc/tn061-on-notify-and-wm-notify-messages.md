---
title: "TN061：ON_NOTIFY 和 WM_NOTIFY 消息 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_NOTIFY"
  - "WM_NOTIFY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通知消息"
  - "ON_NOTIFY 消息"
  - "ON_NOTIFY_EX 消息"
  - "ON_NOTIFY_EX_RANGE 消息"
  - "ON_NOTIFY_RANGE 消息"
  - "TN061"
  - "WM_NOTIFY 消息"
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN061：ON_NOTIFY 和 WM_NOTIFY 消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此技术声明在新的 **WM\_NOTIFY** 消息在 MFC 应用程序提供背景信息和描述处理 **WM\_NOTIFY** 消息建议 \(最常用方法。\)  
  
 **在 Windows 3.x 的控件通知消息**  
  
 在 Windows 3.x 中，控件通过发送消息通知事件 \(例如鼠标单击、更改其父在内容上并选择控件绘制后台给父级。  简单的通知发送作为特殊的 **WM\_COMMAND** 消息，并通知代码 \(如 **BN\_CLICKED**\) 和控件的 ID 将被打包到 `wParam` 和 `lParam`控件的手柄。  注意自 `wParam` 和 `lParam` 为 full，无法将任何附加数据 \- 这些消息可以只简单的通知。  例如，在 **BN\_CLICKED** 通知，无法发送有关鼠标光标的位置的信息时，单击按钮。  
  
 在 Windows 3.x 的控件需要发送包含其他数据的控件通知消息时，会使用的私有信息，包括 `WM_CTLCOLOR`，`WM_VSCROLL`，`WM_HSCROLL`，`WM_DRAWITEM`，`WM_MEASUREITEM`，`WM_COMPAREITEM`，`WM_DELETEITEM`，`WM_CHARTOITEM`，`WM_VKEYTOITEM`，依此类推。  这些消息可以反映回发送自己的控件。  有关更多信息，请参见 [TN062:反射消息窗口的控件](../mfc/tn062-message-reflection-for-windows-controls.md)。  
  
 **在 Win32 的控件通知消息**  
  
 对于显示在 Windows 3.1 中，控件的大多数 Win32 API 使用在 Windows 3.x. 通知消息。  但是，还添加 Win32 许多复杂，复杂控件。该窗口支持的那些 3.x。  通常，这些控件需要发送与其通知消息的其他数据。  而不是添加需要额外数据的每个通知的新 **WM\_\*** 消息，Win32 API 的设计器选择添加一个消息，**WM\_NOTIFY**，可以将任意数量的附加数据一种的标准化方式。  
  
 **WM\_NOTIFY** 消息包含在 `wParam` 发送消息和指针的结构。控件的 ID 设置为 `lParam`。  此结构是 **NMHDR** 或 **NMHDR** 结构具有结构作为其第一的成员数组更大的结构。  请注意，因为 **NMHDR** 成员是第一个，为此结构的指针。可用作指向 **NMHDR** 或的指针为更大的结构的指针。取决于如何转换它。  
  
 在大多数情况下，将指针指向更大的结构，您需要将它转换，如果您在使用它。  在少数通知，如名称以 **NM\_**开始\) 的常见通知 \(和工具提示控件的 **TTN\_SHOW** 和 **TTN\_POP**，通知是实际使用的 **NMHDR** 结构。  
  
 **NMHDR** 结构或最初成员包含发送消息和通知代码控件的句柄和 ID \(如 **TTN\_SHOW**\)。  **NMHDR** 结构的格式如下所示：  
  
```  
typedef struct tagNMHDR {  
    HWND hwndFrom;  
    UINT idFrom;  
    UINT code;  
} NMHDR;  
```  
  
 **TTN\_SHOW** 消息，**代码** 成员将设置为 **TTN\_SHOW**。  
  
 大多数通知将传递指向包含 **NMHDR** 结构作为其第一个成员的更大的结构。  例如，考虑结构使用列表视图控件的 **LVN\_KEYDOWN** 通知消息，发送在键被按下，列表视图控件时。  在 **LV\_KEYDOWN** 结构的指针指向，定义如下所示：  
  
```  
typedef struct tagLV_KEYDOWN {  
    NMHDR hdr;     
    WORD wVKey;    
    UINT flags;    
} LV_KEYDOWN;  
```  
  
 请注意，因为 **NMHDR** 成员是第一个此结构，可以在通知消息传递的指针转换为指向 **NMHDR** 的指针为 **LV\_KEYDOWN**或的指针。  
  
 **通知所有控件共有新窗口**  
  
 某些通知为所有通用的新的 Windows 控件。  这些通知将指向 **NMHDR** 结构。  
  
|通知代码。|由于发送，|  
|-----------|-----------|  
|**NM\_CLICK**|用户单击控件中鼠标左键|  
|**NM\_DBLCLK**|用户双击控件中鼠标左键|  
|**NM\_RCLICK**|用户单击控件中鼠标右键|  
|**NM\_RDBLCLK**|用户双击控件中鼠标右键|  
|**NM\_RETURN**|当控件具有输入焦点时，用户按的 Enter 键|  
|**NM\_SETFOCUS**|使控件的输入焦点|  
|**NM\_KILLFOCUS**|控件失去了输入焦点|  
|**NM\_OUTOFMEMORY**|因为没有足够的内存可，控件无法执行操作|  
  
##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> ON\_NOTIFY:处理在 MFC 应用程序的 WM\_NOTIFY 消息  
 函数处理 `CWnd::OnNotify` 通知消息。  其默认实现检查通知处理程序中处理消息映射可以调用。  通常，不要重写 `OnNotify`。  相反，您提供了处理程序函数并添加该处理程序的消息映射项。所有者窗口的类的信息映射。  
  
 ClassWizard，通过 ClassWizard 属性表，可以创建 `ON_NOTIFY` 消息映射项和提供主干处理程序函数。  有关使用 ClassWizard 的更多信息使此过程更加简单，请参见 [指向函数的信息映射](../mfc/reference/mapping-messages-to-functions.md)。  
  
 `ON_NOTIFY` 消息映射宏具有以下语法：  
  
```  
  
ON_NOTIFY( wNotifyCode, id, memberFxn )  
```  
  
 在斜体的参数替换为：  
  
 `wNotifyCode`  
 通知消息的代码可能需要处理，例如 **LVN\_KEYDOWN**。  
  
 `id`  
 通知发送控件子标识符。  
  
 `memberFxn`  
 当发送通知时，调用成员函数。  
  
 用以下原型声明成员函数：  
  
```  
  
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );  
```  
  
## 备注  
 初始化参数的位置是：  
  
 `pNotifyStruct`  
 到通知结构的指针，如上面一节所述。  
  
 *result*  
 为将要设置的操作结果的指针，则返回。  
  
## 示例  
 若要指定要将成员函数 `OnKeydownList1` 处理从 ID 为 `IDC_LIST1`的 `CListCtrl` 的 **LVN\_KEYDOWN** 消息，使用 ClassWizard 将以下代码添加到消息映射：  
  
```  
ON_NOTIFY( LVN_KEYDOWN, IDC_LIST1, OnKeydownList1 )  
```  
  
 在上面的示例中，类向导提供的函数包括：  
  
```  
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)  
{  
   LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;  
   // TODO: Add your control notification handler  
   //       code here  
  
   *pResult = 0;  
}  
```  
  
 注意 ClassWizard 自动提供适当的类型的指针。  可以通过 `pNMHDR` 或 `pLVKeyDow`通知访问结构。  
  
##  <a name="_mfcnotes_on_notify_range"></a> ON\_NOTIFY\_RANGE  
 如果需要处理一组相同的 **WM\_NOTIFY** 消息控件，可以使用 **ON\_NOTIFY\_RANGE** 而不是 `ON_NOTIFY`。  例如，您可能有一部分需要执行某一条通知消息的操作相同的一组按钮。  
  
 在使用 **ON\_NOTIFY\_RANGE**时，您指定连续范围可以通过指定范围的开头和结尾子标识符处理通知消息的子标识符。  
  
 ClassWizard 不处理 **ON\_NOTIFY\_RANGE**;若要使用，需要编辑消息映射。  
  
 **ON\_NOTIFY\_RANGE** 的消息映射项和函数原型如下：  
  
```  
  
ON_NOTIFY_RANGE(   
wNotifyCode  
,   
id  
,   
idLast  
,   
memberFxn  
 )  
  
```  
  
 在斜体的参数替换为：  
  
 `wNotifyCode`  
 通知消息的代码可能需要处理，例如 **LVN\_KEYDOWN**。  
  
 `id`  
 在连续的范围的第一个标识符标识符。  
  
 `idLast`  
 在连续的范围的最后一个标识符标识符。  
  
 `memberFxn`  
 当发送通知时，调用成员函数。  
  
 用以下原型声明成员函数：  
  
```  
  
afx_msg void memberFxn( UINT id, NMHDR * pNotifyStruct, LRESULT * result );  
```  
  
## 备注  
 初始化参数的位置是：  
  
 `id`  
 发送通知控件子标识符。  
  
 `pNotifyStruct`  
 到通知结构的指针相同，如上面所述。  
  
 *result*  
 为将要设置的操作结果的指针，则返回。  
  
##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON\_NOTIFY\_EX，ON\_NOTIFY\_EX\_RANGE  
 如果希望多个通知传送的对象处理消息，可以使用 **ON\_NOTIFY\_EX** \(或 **ON\_NOTIFY\_EX\_RANGE**\) 而不是 `ON_NOTIFY` \(或 **ON\_NOTIFY\_RANGE**\)。  在 **EX** 版本和常规生成之间的唯一差别用于标记的 **EX** 版本调用的成员函数返回 **BOOL** 消息处理是否应继续。  返回从该函数的 **FALSE** 允许您处理多个对象相同的消息。  
  
 ClassWizard 不处理 **ON\_NOTIFY\_EX** 或 **ON\_NOTIFY\_EX\_RANGE**;如果要使用其中之一，需要编辑消息映射。  
  
 **ON\_NOTIFY\_EX** 的消息映射项和函数原型和\/或 **ON\_NOTIFY\_EX\_RANGE** 如下所示。  参数的含义与非**EX** 版本。  
  
```  
  
ON_NOTIFY_EX( nCode, id, memberFxn ) ON_NOTIFY_EX_RANGE( wNotifyCode, id, idLast, memberFxn )  
```  
  
 两个原型以上相同：  
  
```  
  
afx_msg BOOL memberFxn( UINT id, NMHDR * pNotifyStruct, LRESULT * result );  
```  
  
## 备注  
 在这两种情况下，`id` 包含发送通知控件子标识符。  
  
 函数必须返回 **TRUE**，则通知消息完全处理了或 **FALSE**，则在命令传送的其他对象应有机会处理消息。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)