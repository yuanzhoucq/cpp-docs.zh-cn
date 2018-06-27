---
title: TN062： 消息 Windows 控件的反射 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls.messages
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 683281af3d029dca7e8060bb250a49f8e095d597
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954577"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062：Windows 控件的消息反射
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此技术说明描述消息反射，MFC 4.0 中的新功能。 它还包含有关如何创建使用消息反射中的简单可重用控件。  
  
 此技术说明不讨论消息反射，因为它应用到 ActiveX 控件 （以前称为 OLE 控件）。 请参阅文章[ActiveX 控件： 子类化 Windows 控件](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
 **消息反射是什么**  
  
 Windows 控件经常到其父窗口发送通知消息。 例如，很多控件，将控制颜色通知消息 （WM_CTLCOLOR 或其变化版本之一） 发送到其父以允许父提供用于绘制控件的背景画笔。  
  
 在 Windows 和 MFC 4.0 版之前，父窗口，通常一个对话框，负责处理这些消息。 这意味着，处理消息的代码需要在父窗口类，因此必须在每个类都需要处理该消息中重复。 在上面的示例中，每个想要使用自定义的背景的控件的对话框中将需要处理控件颜色通知消息。 则可以更轻松地重用代码，如果控件类都可以编写，它将处理其自己的背景色。  
  
 在 MFC 4.0 中的旧机制仍然正常工作，父窗口可以处理通知消息。 此外，但是，MFC 4.0 促进重用通过提供一种称为"消息反射"功能允许子控件的窗口或父窗口中，或两者中要处理这些通知消息。 在控件背景的颜色示例中，您现在可以编写通过处理反射的 WM_CTLCOLOR 消息设置其自己的背景颜色的控件类-所有而不依赖于父级。 (请注意，由于消息反射通过 MFC 实现，不由 Windows，父窗口类必须派生自`CWnd`有关消息反射来工作。)  
  
 较旧版本的 MFC 进行了类似于消息反射通过为某些消息，如所有者描述的列表框 （WM_DRAWITEM，等等） 的消息提供虚函数。 新的消息反射机制是通用和一致。  
  
 消息反射是与 4.0 之前的 MFC 版本编写的代码向后兼容。  
  
 如果提供的处理程序特定消息，或者为某个范围的消息，在父窗口的类中，它将替代反映对同一条消息的消息处理程序，提供你不在你自己的处理程序中调用基类处理程序函数。 例如，在对话框类中处理 WM_CTLCOLOR，如果你处理将重写任何反射的消息处理程序。  
  
 仅当发送这些消息的子控件不具有通过反射的消息处理程序，如果在父窗口类中，你提供针对特定的 WM_NOTIFY 消息或范围的 WM_NOTIFY 消息处理程序时，将调用你处理程序`ON_NOTIFY_REFLECT()`。 如果你使用`ON_NOTIFY_REFLECT_EX()`在消息映射中，消息处理程序可能或可能不允许父窗口来处理该消息。 如果处理程序返回**FALSE**，消息将返回的调用时处理，则父级**TRUE**不允许进行处理的父级。 请注意在通知消息前进行处理反射的消息。  
  
 WM_NOTIFY 消息发送时，系统将为控件提供第一个机会处理它。 如果任何其他反映的消息发送时，父窗口具有第一个机会处理它，并且该控件将接收反射的消息。 若要执行此操作，它将需要处理程序函数和控件的类消息映射中的相应条目。  
  
 反映的消息的消息映射宏是正则通知稍有不同： 它具有 *_REFLECT*追加到其常用的名称。 例如，若要处理的父代中的 WM_NOTIFY 消息，你可以使用在父级的消息映射宏 ON_NOTIFY。 若要处理反射的消息中的子控件，请在子控件的消息映射中使用 ON_NOTIFY_REFLECT 宏。 在某些情况下，参数不同，也是的。 请注意，ClassWizard 可以通常会为您添加的消息映射条目，并且提供用正确的参数的主干函数实现。  
  
 请参阅[TN061: ON_NOTIFY 和 WM_NOTIFY 消息](../mfc/tn061-on-notify-and-wm-notify-messages.md)有关新的 WM_NOTIFY 消息的信息。  
  
 **消息映射项和处理程序函数原型，以便反映的消息**  
  
 若要处理反映的控件通知消息，使用的消息映射宏和下表中列出的函数原型。  
  
 通常，ClassWizard 可以为您添加这些消息映射条目，并提供主干函数实现。 请参阅[反映的消息定义消息处理程序](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)有关如何定义反映的消息的处理程序的信息。  
  
 若要从消息名称转换为反映的宏名称，在前面添加*ON_* 和追加 *_REFLECT*。 例如，WM_CTLCOLOR 将成为 ON_WM_CTLCOLOR_REFLECT。 （若要查看可以反映的消息，请执行下表中的宏项相反的转换。）  
  
 上述规则的三个例外是，如下所示：  
  
-   WM_COMMAND 通知宏是 ON_CONTROL_REFLECT。  
  
-   WM_NOTIFY 反射宏是 ON_NOTIFY_REFLECT。  
  
-   ON_UPDATE_COMMAND_UI 反射宏是 ON_UPDATE_COMMAND_UI_REFLECT。  
  
 在每个以上的特殊情况下，你必须指定处理程序成员函数的名称。 在其他情况下，你必须使用您的处理程序的标准名称。  
  
 参数的含义和函数返回值都记录在函数名称或函数名称加上下*上*预置。 例如，`CtlColor`中所述`OnCtlColor`。 多个反射的消息处理程序需要比在父窗口中的类似处理较少的参数。 只需与下表中的文档中的正式参数名称的名称匹配。  
  
|映射条目|函数原型|  
|---------------|------------------------|  
|**ON_CONTROL_REFLECT (** `wNotifyCode` **，** `memberFxn` **)**|**afx_msg void** `memberFxn` **（);**|  
|**ON_NOTIFY_REFLECT (** `wNotifyCode` **，** `memberFxn` **)**|**afx_msg void** `memberFxn` **(NMHDR \***  `pNotifyStruct` **，LRESULT\***  *结果* **);**|  
|**ON_UPDATE_COMMAND_UI_REFLECT (** `memberFxn` **)**|**afx_msg void** `memberFxn` **(CCmdUI\***  `pCmdUI` **);**|  
|**ON_WM_CTLCOLOR_REFLECT （)**|**afx_msg HBRUSH CtlColor (CDC\***  `pDC` **，UINT** `nCtlColor` **);**|  
|**ON_WM_DRAWITEM_REFLECT （)**|**afx_msg void DrawItem (LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|  
|**ON_WM_MEASUREITEM_REFLECT （)**|**afx_msg void MeasureItem (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|  
|**ON_WM_DELETEITEM_REFLECT （)**|**afx_msg void DeleteItem (LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|  
|**ON_WM_COMPAREITEM_REFLECT （)**|**afx_msg int CompareItem (LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|  
|**ON_WM_CHARTOITEM_REFLECT （)**|**afx_msg int CharToItem (UINT** `nKey` **，UINT** `nIndex` **);**|  
|**ON_WM_VKEYTOITEM_REFLECT （)**|**afx_msg int VKeyToItem (UINT** `nKey` **，UINT** `nIndex` **);**|  
|**ON_WM_HSCROLL_REFLECT （)**|**afx_msg void HScroll (UINT** `nSBCode` **，UINT** `nPos` **);**|  
|**ON_WM_VSCROLL_REFLECT （)**|**afx_msg void VScroll (UINT** `nSBCode` **，UINT** `nPos` **);**|  
|**ON_WM_PARENTNOTIFY_REFLECT （)**|**afx_msg void ParentNotify (UINT** `message` **，LPARAM** `lParam` **);**|  
  
 ON_NOTIFY_REFLECT 和 ON_CONTROL_REFLECT 宏具有允许多个对象 （如控件和其父级） 来处理指定的消息的变体。  
  
|映射条目|函数原型|  
|---------------|------------------------|  
|**ON_NOTIFY_REFLECT_EX (** `wNotifyCode` **，** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **(NMHDR \***  `pNotifyStruct` **，LRESULT\***  *结果* **);**|  
|**ON_CONTROL_REFLECT_EX (** `wNotifyCode` **，** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **（);**|  
  
## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>处理反映消息： 可重用控件的示例  
 这个简单的示例创建名为的可重用控件`CYellowEdit`。 控件工作的正则编辑控件相同，区别在于它会显示黄色背景上的黑色文本。 它可以轻松地添加成员函数，这会让`CYellowEdit`控件来显示不同的颜色。  
  
#### <a name="to-try-the-example-that-creates-a-reusable-control"></a>若要试用创建可重用控件示例  
  
1.  在现有应用程序中创建一个新的对话框。 有关详细信息，请参阅[对话框编辑器](../windows/dialog-editor.md)主题。  
  
     你必须具有用于开发可重用控件中的应用程序。 如果你没有现有应用程序使用，创建使用应用程序向导的、 基于对话框的应用程序。  
  
2.  加载到 Visual c + + 项目，使用类向导创建新的类称为`CYellowEdit`基于`CEdit`。  
  
3.  三个成员将变量添加到你`CYellowEdit`类。 前两个将*COLORREF*变量以保存的文本颜色和背景色。 将第三个`CBrush`将保存用于绘制背景的画笔的对象。 `CBrush`对象允许你创建一次，只是引用它之后的画笔并时自动销毁画笔`CYellowEdit`销毁控件。  
  
4.  如下所示编写构造函数中初始化成员变量：  
  
 ```  
    CYellowEdit::CYellowEdit() 
 {  
    m_clrText = RGB(0,
    0,
    0);

    m_clrBkgnd = RGB(255,
    255,
    0);

    m_brBkgnd.CreateSolidBrush(m_clrBkgnd);

 }  
 ```  
  
5.  使用类向导，将添加到的反射 WM_CTLCOLOR 消息处理程序你`CYellowEdit`类。 请注意，你可以处理的消息列表中的消息名称的前面等号指示该消息将反映。 这中所述[反映的消息定义消息处理程序](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)。  
  
     类向导为您添加下面的消息映射宏和主干函数：  
  
 ```  
    ON_WM_CTLCOLOR_REFLECT() 
 *// Note: other code will be in between....  
 
    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)   
 { *// TODO: Change any attributes of the DC here  
 *// TODO: Return a non-NULL brush if the *//   parent's handler should not be called  
    return NULL;  
 }  
 ```  
  
6.  函数的正文替换为下面的代码。 该代码指定的文本颜色、 文本背景色和 rest 的控件的背景色。  
  
 ```  
    pDC->SetTextColor(m_clrText);
*// text  
    pDC->SetBkColor(m_clrBkgnd);
*// text bkgnd  
    return m_brBkgnd;            // ctl bkgnd  
 ```  
  
7.  在对话框中，创建一个编辑控件，然后将其附加到成员变量通过按住 control 密钥并向下双击编辑控件。 在添加成员变量对话框中，完成变量的名称和类别，然后"CYellowEdit"变量的类型选择"控件"。 不要忘记在对话框中设置 tab 键顺序。 此外，一定要包括的头文件`CYellowEdit`对话框中的标头文件中的控件。  
  
8.  生成并运行应用程序。 编辑控件将具有黄色背景。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

