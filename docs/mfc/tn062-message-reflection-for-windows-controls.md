---
title: "TN062：Windows 控件的消息反射 | Microsoft Docs"
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
  - "vc.controls.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "消息反射"
  - "通知消息"
  - "ON_CONTROL_REFLECT 宏"
  - "ON_CONTROL_REFLECT_EX 宏"
  - "ON_NOTIFY 消息"
  - "ON_NOTIFY_REFLECT 消息"
  - "ON_NOTIFY_REFLECT_EX 消息"
  - "ON_UPDATE_COMMAND_UI_REFLECT 宏"
  - "ON_WM_CHARTOITEM_REFLECT 宏"
  - "ON_WM_COMPAREITEM_REFLECT 宏"
  - "ON_WM_CTLCOLOR_REFLECT 宏"
  - "ON_WM_DELETEITEM_REFLECT 宏"
  - "ON_WM_DRAWITEM_REFLECT 宏"
  - "ON_WM_HSCROLL_REFLECT 宏"
  - "ON_WM_MEASUREITEM_REFLECT 宏"
  - "ON_WM_PARENTNOTIFY_REFLECT 宏"
  - "ON_WM_VKEYTOITEM_REFLECT 宏"
  - "ON_WM_VSCROLL_REFLECT 宏"
  - "TN062"
  - "WM_COMMAND"
  - "WM_CTLCOLOR 消息"
  - "WM_NOTIFY 消息"
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN062：Windows 控件的消息反射
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此技术声明介绍反射消息，在 MFC 4.0 的新功能。  它还包含创建使用消息反射的一个简单的可重用控件的方向。  
  
 此技术声明不讨论反射消息时，该应用于 ActiveX 控件 \(以前调用 OLE 控件\)。   参见文章 [ActiveX 控件：的 Subclassing 窗口控制](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
 **消息反射是什么？**  
  
 Windows 控件频繁发送通知消息到其父窗口。  例如，许多控件颜色控件发送通知消息 \(其变量或`WM_CTLCOLOR` 之一\) 向其父允许父提供绘制控件的背景的画笔。  
  
 在窗口和在 4.0 版之前的 MFC，父窗口，通常，对话框负责处理这些信息。  这意味着的消息处理代码需要在父窗口的类，并且在需要处理该消息的每类必须复制。  采用上面的示例中，每一对话框具有自定义背景的需要的控件必须处理控件颜色通知消息。  重用代码要容易的多，如果要处理自己的背景色的控件类可能编写。  
  
 在 MFC 4.0，旧机制仍然工作 \- 父窗口可以处理控件通知消息。  此外，但是，MFC 4.0 实现重用通过提供调用“子控件窗口或父窗口使这些通知消息已得到处理的反射消息”功能，或者在两个。  在控件背景色的示例中，您现在可以编写通过处理反映的 `WM_CTLCOLOR` 消息为自己设置的背景颜色 \- 所有无需依赖父的控件类。（注释因为消息反射由 MFC 实现，而不是必须的反射消息窗口中，从 `CWnd` 派生可以工作的父窗口类。）  
  
 MFC 旧的版本执行操作类似于反射消息提供通过虚函数为某些消息，例如列表框的所有者描述 \(`WM_DRAWITEM`消息，等等\)。  新消息反射机制是通用和一致。  
  
 反射是消息与 MFC 版本的向后兼容 4.0 在编写代码之前。  
  
 如果您提供了处理程序的值的消息特定消息，或域，在父窗口的类，则将重写反映了相同的消息的消息处理程序提供了您不调用基类中函数处理程序自己的处理程序。  例如，如果您处理对话框类中的 `WM_CTLCOLOR`，用于处理要重写任何反射消息处理程序。  
  
 如果，在父窗口类，接下来提供特定的 **WM\_NOTIFY** 消息或字符范围中的 **WM\_NOTIFY** 消息处理程序，处理程序将调用，才发送这些消息的子控件没通过 **ON\_NOTIFY\_REFLECT\(\)**具有反射消息处理程序。  如果在消息映射使用 **ON\_NOTIFY\_REFLECT\_EX\(\)**，消息处理程序也可能不允许父窗口处理消息。  如果处理程序返回 **FALSE**，消息将由父级处理，而 **TRUE** 的调用不返回，允许父元素处理它。  注意反射消息在通知消息之前进行处理。  
  
 当 **WM\_NOTIFY** 发送时，控件提供第一个机会处理它。  如果其他反射的信息发送，父窗口具有第一个机会处理它，然后控件将收到反射消息。  为此，在控件类的信息映射需要处理程序函数和适当的输入。  
  
 反射消息的消息映射宏为某些通知行为不同：它通常具有 **\_REFLECT** 追加到其名称。  例如，处理将在父的 **WM\_NOTIFY** 消息，可以在父的消息映射使用 `ON_NOTIFY` 宏。  若要处理在子控件的反射消息，请使用 **ON\_NOTIFY\_REFLECT** 宏在子控件的消息映射。  有时，参数不同。  注意 ClassWizard 通常可以添加您的消息映射项和提供摘要函数实现以正确的参数。  
  
 有关新的 **WM\_NOTIFY** 消息的信息，请参见 [TN061:ON\_NOTIFY 和 WM\_NOTIFY 消息](../mfc/tn061-on-notify-and-wm-notify-messages.md)。  
  
 **输入和消息映射处理程序函数原型反映的消息**  
  
 若要处理中反映的控件通知消息，使用宏和消息映射函数原型在下表中列出。  
  
 ClassWizard 通常可以将这些消息映射项和提供摘要函数的实现。  有关如何定义反射消息的处理程序的信息，请参见 [为反射消息定义的消息处理程序](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)。  
  
 从消息名称若要转换为反映的宏名称，请添加在前面追加 **ON\_** 和 **\_REFLECT**。  例如，`WM_CTLCOLOR` 成为 **ON\_WM\_CTLCOLOR\_REFLECT**。\(显示的信息可能反映，请在宏执行输入相反的转换在下表中。\)  
  
 为上述规则的三以下情况例外：  
  
-   **WM\_COMMAND** 通知的宏为 **ON\_CONTROL\_REFLECT**。  
  
-   反射 **WM\_NOTIFY** 的宏为 **ON\_NOTIFY\_REFLECT**。  
  
-   `ON_UPDATE_COMMAND_UI` 反映的是 **ON\_UPDATE\_COMMAND\_UI\_REFLECT**宏。  
  
 在上述每一个特例，必须指定成员处理程序函数的名称。  在其他情况下，您必须为函数处理程序使用标准名称。  
  
 函数的参数和返回值的含义文档在或函数名称下或者使用 **开** 的函数名加上了在前面。  例如，**CtlColor** 将在 `OnCtlColor`文档。  若干反射消息处理程序在比父窗口相同的处理程序所需的参数。  只需对名称在下面的表提供形参名称的文档中。  
  
|映射项|函数原型|  
|---------|----------|  
|**ON\_CONTROL\_REFLECT\(**  `wNotifyCode` **,**  `memberFxn` **\)**|**afx\_msg void**  `memberFxn`  **\( \);**|  
|**ON\_NOTIFY\_REFLECT\(**  `wNotifyCode` **,**  `memberFxn` **\)**|**afx\_msg void**  `memberFxn`  **\( NMHDR \***  `pNotifyStruct` **, LRESULT\***  *结果*  **\);**|  
|**ON\_UPDATE\_COMMAND\_UI\_REFLECT\(**  `memberFxn` **\)**|**afx\_msg void**  `memberFxn`  **\( CCmdUI\***  `pCmdUI`  **\);**|  
|**ON\_WM\_CTLCOLOR\_REFLECT\( \)**|**afx\_msg HBRUSH CtlColor \( CDC\***  `pDC` **, UINT**  `nCtlColor`  **\);**|  
|**ON\_WM\_DRAWITEM\_REFLECT\( \)**|**afx\_msg void DrawItem \( LPDRAWITEMSTRUCT** `lpDrawItemStruct`  **\);**|  
|**ON\_WM\_MEASUREITEM\_REFLECT\( \)**|**afx\_msg void MeasureItem \( LPMEASUREITEMSTRUCT**  `lpMeasureItemStruct`  **\);**|  
|**ON\_WM\_DELETEITEM\_REFLECT\( \)**|**afx\_msg void DeleteItem \( LPDELETEITEMSTRUCT**  `lpDeleteItemStruct`  **\);**|  
|**ON\_WM\_COMPAREITEM\_REFLECT\( \)**|**afx\_msg int CompareItem \( LPCOMPAREITEMSTRUCT**  `lpCompareItemStruct`  **\);**|  
|**ON\_WM\_CHARTOITEM\_REFLECT\( \)**|**afx\_msg int CharToItem \( UINT**  `nKey` **, UINT**  `nIndex`  **\);**|  
|**ON\_WM\_VKEYTOITEM\_REFLECT\( \)**|**afx\_msg int VKeyToItem \( UINT**  `nKey` **, UINT**  `nIndex`  **\);**|  
|**ON\_WM\_HSCROLL\_REFLECT\( \)**|**afx\_msg void HScroll \( UINT**  `nSBCode` **, UINT**  `nPos`  **\);**|  
|**ON\_WM\_VSCROLL\_REFLECT\( \)**|**afx\_msg void VScroll \( UINT**  `nSBCode` **, UINT**  `nPos`  **\);**|  
|**ON\_WM\_PARENTNOTIFY\_REFLECT\( \)**|**afx\_msg void ParentNotify \( UINT**  `message` **, LPARAM**  `lParam`  **\);**|  
  
 **ON\_NOTIFY\_REFLECT** 和 **ON\_CONTROL\_REFLECT** 宏具有允许多个对象中的变体 \(如控件及其父级\) 处理已提供的信息。  
  
|映射项|函数原型|  
|---------|----------|  
|**ON\_NOTIFY\_REFLECT\_EX\(**  `wNotifyCode` **,**  `memberFxn` **\)**|**afx\_msg BOOL**  `memberFxn`  **\( NMHDR \***  `pNotifyStruct` **, LRESULT\***  *结果*  **\);**|  
|**ON\_CONTROL\_REFLECT\_EX\(**  `wNotifyCode` **,**  `memberFxn`  **\)**|**afx\_msg BOOL**  `memberFxn`  **\( \);**|  
  
## 处理反射消息：可重用控件的示例  
 此简单示例创建一个名为 `CYellowEdit`的可重用控件。  控件有效与标准编辑控件相同，但它在黄色背景的黑色文本。  添加将允许 `CYellowEdit` 控件显示的不同颜色的成员函数非常容易。  
  
#### 尝试创建可重用的控件的示例  
  
1.  创建在一个现有的应用程序的对话框。  有关详细信息，请参阅 [窗口编辑器](../mfc/dialog-editor.md) 接口主题。  
  
     您必须对开发可重用控件的应用程序。  如果不需要使用一种现有的应用程序，使用 AppWizard，创建了基于对话框的应用程序。  
  
2.  在项目加载到 Visual C\+\+，请使用类向导基于 `CEdit`创建名为 `CYellowEdit` 的新类。  
  
3.  添加三的成员变量添加到 `CYellowEdit` 类。  之前都为保持文本颜色和背景色的 **COLORREF** 变量。  第三将会保存绘制背景画笔的 `CBrush` 对象。  当销毁时，`CBrush` 对象您允许将一次创建画笔，仅引用它。此后和自动销毁画笔 `CYellowEdit` 控件。  
  
4.  通过将构造函数初始化成员变量：  
  
    ```  
    CYellowEdit::CYellowEdit()  
    {  
       m_clrText = RGB( 0, 0, 0 );  
       m_clrBkgnd = RGB( 255, 255, 0 );  
       m_brBkgnd.CreateSolidBrush( m_clrBkgnd );  
    }  
    ```  
  
5.  使用 ClassWizard，请添加反射的 `WM_CTLCOLOR` 消息处理程序添加到 `CYellowEdit` 类。  请注意光标消息名称前面的等号中可以处理消息的列表以指示该消息已得到反映。  这在中描述。[为反射消息定义的消息处理程序](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)  
  
     ClassWizard 添加下面消息映射宏和函数的主干：  
  
    ```  
    ON_WM_CTLCOLOR_REFLECT()  
  
    // Note: other code will be in between....  
  
    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)   
    {  
       // TODO: Change any attributes of the DC here  
  
       // TODO: Return a non-NULL brush if the  
       //   parent's handler should not be called  
       return NULL;  
    }  
    ```  
  
6.  将函数的主体的代码替换为以下代码：  代码对于其他控件指定文本颜色、文本背景色和背景色。  
  
    ```  
    pDC->SetTextColor( m_clrText );   // text  
    pDC->SetBkColor( m_clrBkgnd );   // text bkgnd  
    return m_brBkgnd;            // ctl bkgnd  
    ```  
  
7.  在创建对话框中的 Edit 控件，然后附加到成员变量双击编辑控件，按住 Ctrl 键按下时。  在"添加成员变量"对话框，请完成变量名称并选择“控件”类别，然后“CYellowEdit”变量的类型。  不要忘记设置对话框中的 Tab 键顺序。  此外，确保到包含 `CYellowEdit` 控件的标头文件对话框中的头文件。  
  
8.  生成并运行应用程序。  编辑控件将以黄色背景。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)