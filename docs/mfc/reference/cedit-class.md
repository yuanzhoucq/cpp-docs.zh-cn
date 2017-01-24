---
title: "CEdit Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CEdit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEdit class"
  - "控件 [MFC], edit"
  - "edit controls"
  - "edit controls, 类"
  - "line separators in multiline edit controls"
  - "multiline edit control"
  - "分隔符, in multiline edit controls"
  - "text editors"
  - "text editors, CEdit class"
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
caps.latest.revision: 22
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CEdit Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows的功能编辑控件。  
  
## 语法  
  
```  
class CEdit : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CEdit::CEdit](../Topic/CEdit::CEdit.md)|构造 `CEdit` 控件对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CEdit::CanUndo](../Topic/CEdit::CanUndo.md)|确定编辑控件操作是否可以取消。|  
|[CEdit::CharFromPos](../Topic/CEdit::CharFromPos.md)|检索字符的行和字符的索引最接近一个指定的位置。|  
|[CEdit::Clear](../Topic/CEdit::Clear.md)|删除（清除）当前选定内容（如果有）在编辑控件。|  
|[CEdit::Copy](../Topic/CEdit::Copy.md)|复制当前选定内容（如果有）在编辑控件到剪贴板中 **CF\_TEXT** 格式。|  
|[CEdit::Create](../Topic/CEdit::Create.md)|创建Windows编辑控件并将它附加到 `CEdit` 对象。|  
|[CEdit::Cut](../Topic/CEdit::Cut.md)|删除\(剪辑\)当前选定内容（如果有）在编辑控件和复制已删除的文本复制到剪贴板 **CF\_TEXT** 格式。|  
|[CEdit::EmptyUndoBuffer](../Topic/CEdit::EmptyUndoBuffer.md)|重置\(清除\)编辑控件的取消标记。|  
|[CEdit::FmtLines](../Topic/CEdit::FmtLines.md)|设置柔和换行符包括开\/关在多行中编辑控件。|  
|[CEdit::GetCueBanner](../Topic/CEdit::GetCueBanner.md)|检索显示为文本提示的文本，或者提示，在编辑控件，该控件为空，并且没有焦点时。|  
|[CEdit::GetFirstVisibleLine](../Topic/CEdit::GetFirstVisibleLine.md)|确定编辑控件的最顶层的可见的行。|  
|[CEdit::GetHandle](../Topic/CEdit::GetHandle.md)|检索处理为多行当前分配编辑控件的内存。|  
|[CEdit::GetHighlight](../Topic/CEdit::GetHighlight.md)|获取开始的索引，然后在当前显示的文本范围的结束字符编辑控件。|  
|[CEdit::GetLimitText](../Topic/CEdit::GetLimitText.md)|获取此 `CEdit` 包含的最大数量文本。|  
|[CEdit::GetLine](../Topic/CEdit::GetLine.md)|从edit控件检索文本行。|  
|[CEdit::GetLineCount](../Topic/CEdit::GetLineCount.md)|检索的行数在多行编辑控件的。|  
|[CEdit::GetMargins](../Topic/CEdit::GetMargins.md)|获取此 `CEdit`的左右边距。|  
|[CEdit::GetModify](../Topic/CEdit::GetModify.md)|确定是否已修改编辑控件的内容。|  
|[CEdit::GetPasswordChar](../Topic/CEdit::GetPasswordChar.md)|在用户输入文本时，检索在编辑控件显示的密码字符。|  
|[CEdit::GetRect](../Topic/CEdit::GetRect.md)|获取编辑器控件的格式设置矩形。|  
|[CEdit::GetSel](../Topic/CEdit::GetSel.md)|获取当前选择的第一个和最后一个字符位置在编辑控件。|  
|[CEdit::HideBalloonTip](../Topic/CEdit::HideBalloonTip.md)|隐藏所有气球状提示与当前编辑控件。|  
|[CEdit::LimitText](../Topic/CEdit::LimitText.md)|限制用户可以输入编辑控件的文本长度。|  
|[CEdit::LineFromChar](../Topic/CEdit::LineFromChar.md)|检索包含指定的字符的索引行的行号。|  
|[CEdit::LineIndex](../Topic/CEdit::LineIndex.md)|检索一行索引在多行中的edit控件的字符。|  
|[CEdit::LineLength](../Topic/CEdit::LineLength.md)|检索一行的长度在编辑控件中。|  
|[CEdit::LineScroll](../Topic/CEdit::LineScroll.md)|将文本多行编辑控件。|  
|[CEdit::Paste](../Topic/CEdit::Paste.md)|从剪贴板中的数据到当前光标的编辑控件中确定的插入。  数据，仅当剪贴板在 **CF\_TEXT** 格式，包含数据插入。|  
|[CEdit::PosFromChar](../Topic/CEdit::PosFromChar.md)|检索指定的字符索引的左上角的坐标。|  
|[CEdit::ReplaceSel](../Topic/CEdit::ReplaceSel.md)|以指定文本替换在编辑控件中当前选择。|  
|[CEdit::SetCueBanner](../Topic/CEdit::SetCueBanner.md)|设置显示为文本提示的文本，或者提示，在编辑控件，该控件为空，并且没有焦点时。|  
|[CEdit::SetHandle](../Topic/CEdit::SetHandle.md)|设置句柄将由使用多行编辑控件的本地内存中。|  
|[CEdit::SetHighlight](../Topic/CEdit::SetHighlight.md)|显示当前所显示编辑控件的文本范围。|  
|[CEdit::SetLimitText](../Topic/CEdit::SetLimitText.md)|将此 `CEdit` 包含的最大数量文本。|  
|[CEdit::SetMargins](../Topic/CEdit::SetMargins.md)|将此 `CEdit`的左右边距。|  
|[CEdit::SetModify](../Topic/CEdit::SetModify.md)|设置或清除编辑控件修改标志。|  
|[CEdit::SetPasswordChar](../Topic/CEdit::SetPasswordChar.md)|在用户输入文本时，设置或移除在编辑控件显示的密码字符。|  
|[CEdit::SetReadOnly](../Topic/CEdit::SetReadOnly.md)|设置编辑控件的只读状态。|  
|[CEdit::SetRect](../Topic/CEdit::SetRect.md)|设置格式化矩形多行编辑控件和更新的控件。|  
|[CEdit::SetRectNP](../Topic/CEdit::SetRectNP.md)|设置格式化矩形多行编辑控件，而无需重绘控件的窗口。|  
|[CEdit::SetSel](../Topic/CEdit::SetSel.md)|选择字符的范围在编辑控件中。|  
|[CEdit::SetTabStops](../Topic/CEdit::SetTabStops.md)|设置在多行的制表位编辑控件。|  
|[CEdit::ShowBalloonTip](../Topic/CEdit::ShowBalloonTip.md)|显示与当前编辑控件的气球状提示。|  
|[CEdit::Undo](../Topic/CEdit::Undo.md)|反转最后一个编辑控件操作。|  
  
## 备注  
 编辑控件是用户可以输入文本的矩形子窗口。  
  
 可以创建编辑控件从对话框模板或直接在代码。  在这两种情况下，首次调用构造函数 `CEdit` 构造 `CEdit` 对象，然后调用 [创建](../Topic/CEdit::Create.md) 成员函数创建Windows编辑控件并将它附加到 `CEdit` 对象。  
  
 构造。`CEdit`从派生的类可以选件一步过程。  编写该派生类的构造函数和调用 **Create** 从构造函数内部。  
  
 `CEdit` 继承 `CWnd`的重要功能。  从 `CEdit` 对象若要设置和检索文本，请使用 `CWnd` 成员函数 [SetWindowText](../Topic/CWnd::SetWindowText.md) 和 [GetWindowText](../Topic/CWnd::GetWindowText.md)，设置或获取编辑控件的整个内容，因此，即使它是一个多行控件。  在多行控件的文本行被“\\ r \\ n字符序列分隔。  此外，如果该编辑控件是多行，get和控件的文本设置的一部分通过调用 `CEdit` 成员函数 [GetLine](../Topic/CEdit::GetLine.md)，[SetSel](../Topic/CEdit::SetSel.md)、 [GetSel](../Topic/CEdit::GetSel.md)和 [ReplaceSel](../Topic/CEdit::ReplaceSel.md)。  
  
 如果希望处理Windows编辑控件发送的通知消息到其父\(通常从 `CDialog`派生的选件类\)中，添加一个消息映射项和消息处理程序成员函数为每个消息的父选件类。  
  
 每个消息映射项采用以下形式:  
  
 **ON\_**通知**\(***ID，memberFxn***\)**  
  
 其中 `id` 指定发送的编辑控件的MDI子窗口ID通知和 `memberFxn` 是您处理编写通知父成员函数的名称。  
  
 父的函数原型如下所示:  
  
 **afx\_msg** 无效memberFxn**\( \);**  
  
 以下潜在的消息映射项及其将发送到父用例说明的列表:  
  
-   **ON\_EN\_CHANGE** 用户获得的可能修改了在编辑控件的文本的操作。  不同 **EN\_UPDATE** 通知消息，此通知信息在Windows更新后发送该显示。  
  
-   **ON\_EN\_ERRSPACE** 编辑控件不能分配的内存量已经足以满足特定请求。  
  
-   **ON\_EN\_HSCROLL** 用户单击编辑控件的水平滚动条。  在屏幕更新之前，父窗口收到通知。  
  
-   **ON\_EN\_KILLFOCUS** 编辑控件失去输入焦点。  
  
-   **ON\_EN\_MAXTEXT** 当前插入超出了字符指定数目的编辑控件的和被截断。  并将在编辑控件没有时 **ES\_AUTOHSCROLL** 样式和要插入的字符数会超过编辑控件的宽度。  并将在编辑控件没有时 **ES\_AUTOVSCROLL** 样式和行的总数由文本插入将超出编辑控件的高度。  
  
-   **ON\_EN\_SETFOCUS** 发送的编辑控件时接收输入焦点。  
  
-   **ON\_EN\_UPDATE** 编辑控件将显示修改后的文本。  发送，控件格式化文本后，该但是，在屏幕文本，才能使窗口大小进行修改，如果需要。  
  
-   **ON\_EN\_VSCROLL** 用户单击编辑控件的垂直滚动条。  在屏幕更新之前，父窗口收到通知。  
  
 如果要创建在对话框中的一 `CEdit` 对象，自动销毁 `CEdit` 对象，当用户关闭对话框时。  
  
 使用对话框编辑器，如果您创建从对话框资源的一 `CEdit` 对象，自动销毁 `CEdit` 对象，当用户关闭对话框时。  
  
 如果在中创建的一 `CEdit` 对象，您可能还需要销毁它。  如果在堆栈上创建 `CEdit` 对象，自动销毁它。  使用 **new** 功能，如果要创建在堆的 `CEdit` 对象，则必须对对象的 **delete** 销毁它，当用户停止Windows编辑控件。  如果将在 `CEdit` 对象的任何内存，请重写 `CEdit` 析构函数进程分配。  
  
 若要修改在编辑控件的某些样式\(例如 **ES\_READONLY**\)必须发送特定信息到控件而不是使用 [ModifyStyle](../Topic/CWnd::ModifyStyle.md)。  在参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [编辑控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775464)。  
  
 有关 `CEdit`的更多信息，请参见:  
  
-   [控件](../../mfc/controls-mfc.md)  
  
-   知识库文章 Q259949：INFO: SetCaretPos\(\) 不合适与 CEdit 或 CRichEditCtrl 控件  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CEdit`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC示例CALCDRIV](../../top/visual-cpp-samples.md)   
 [MFC示例CMNCTRL2](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)