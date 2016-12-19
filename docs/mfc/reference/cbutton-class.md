---
title: "CButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "button control [MFC]"
  - "button objects (CButton)"
  - "CButton class"
  - "复选框, button controls"
  - "checkbox buttons"
  - "pushbuttons"
  - "单选按钮, CButton class"
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
caps.latest.revision: 19
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows按钮控件的功能。  
  
## 语法  
  
```  
class CButton : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CButton::CButton](../Topic/CButton::CButton.md)|构造 `CButton` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CButton::Create](../Topic/CButton::Create.md)|创建Windows按钮控件并将它附加到 `CButton` 对象。|  
|[CButton::DrawItem](../Topic/CButton::DrawItem.md)|重写绘制一个所有者绘制的 `CButton` 对象。|  
|[CButton::GetBitmap](../Topic/CButton::GetBitmap.md)|检索位图的处理之前设置与 [SetBitmap](../Topic/CButton::SetBitmap.md)。|  
|[CButton::GetButtonStyle](../Topic/CButton::GetButtonStyle.md)|检索有关按钮控件样式的信息。|  
|[CButton::GetCheck](../Topic/CButton::GetCheck.md)|检索按钮控件的复选状态。|  
|[CButton::GetCursor](../Topic/CButton::GetCursor.md)|检索光标图像的句柄之前设置与 [SetCursor](../Topic/CButton::SetCursor.md)。|  
|[CButton::GetIcon](../Topic/CButton::GetIcon.md)|检索图标句柄之前设置与 [SetIcon](../Topic/CButton::SetIcon.md)。|  
|[CButton::GetIdealSize](../Topic/CButton::GetIdealSize.md)|检索按钮控件的理想的大小。|  
|[CButton::GetImageList](../Topic/CButton::GetImageList.md)|检索图像列表按钮控件。|  
|[CButton::GetNote](../Topic/CButton::GetNote.md)|检索当前命令链接控件的说明元素。|  
|[CButton::GetNoteLength](../Topic/CButton::GetNoteLength.md)|检索批注文本的长度当前命令链接控件的。|  
|[CButton::GetSplitGlyph](../Topic/CButton::GetSplitGlyph.md)|检索标志符号与当前拆分按钮控件。|  
|[CButton::GetSplitImageList](../Topic/CButton::GetSplitImageList.md)|检索图像为当前拆分按钮控件的列表。|  
|[CButton::GetSplitInfo](../Topic/CButton::GetSplitInfo.md)|检索定义当前拆分按钮控件的信息。|  
|[CButton::GetSplitSize](../Topic/CButton::GetSplitSize.md)|检索当前拆分按钮控件的下拉式元素的边框。|  
|[CButton::GetSplitStyle](../Topic/CButton::GetSplitStyle.md)|检索定义当前拆分按钮控件的拆分按钮样式。|  
|[CButton::GetState](../Topic/CButton::GetState.md)|检索检查状态、突出显示状态和按钮控件的焦点状态。|  
|[CButton::GetTextMargin](../Topic/CButton::GetTextMargin.md)|检索按钮控件的文本边距。|  
|[CButton::SetBitmap](../Topic/CButton::SetBitmap.md)|指定在按钮中显示的位图。|  
|[CButton::SetButtonStyle](../Topic/CButton::SetButtonStyle.md)|更改按钮的样式。|  
|[CButton::SetCheck](../Topic/CButton::SetCheck.md)|将按钮控件的复选状态。|  
|[CButton::SetCursor](../Topic/CButton::SetCursor.md)|指定在按钮中显示的光标图像。|  
|[CButton::SetDropDownState](../Topic/CButton::SetDropDownState.md)|设置当前拆分按钮控件的下拉式状态。|  
|[CButton::SetIcon](../Topic/CButton::SetIcon.md)|指定在按钮中显示的图标。|  
|[CButton::SetImageList](../Topic/CButton::SetImageList.md)|设置图像列表按钮控件。|  
|[CButton::SetNote](../Topic/CButton::SetNote.md)|设置有关当前命令链接控件的说明。|  
|[CButton::SetSplitGlyph](../Topic/CButton::SetSplitGlyph.md)|将指定的标志符号与当前拆分按钮控件。|  
|[CButton::SetSplitImageList](../Topic/CButton::SetSplitImageList.md)|关联图像列表与当前拆分按钮控件。|  
|[CButton::SetSplitInfo](../Topic/CButton::SetSplitInfo.md)|指定定义当前拆分按钮控件的信息。|  
|[CButton::SetSplitSize](../Topic/CButton::SetSplitSize.md)|设置当前拆分按钮控件的下拉式元素的边框。|  
|[CButton::SetSplitStyle](../Topic/CButton::SetSplitStyle.md)|设置当前拆分按钮控件的样式。|  
|[CButton::SetState](../Topic/CButton::SetState.md)|将按钮控件的显示的状态。|  
|[CButton::SetTextMargin](../Topic/CButton::SetTextMargin.md)|将按钮控件的文本边距。|  
  
## 备注  
 按钮控件是可以打开单击的小矩形，子窗口。  按钮单独使用或在组中，并可通过标记或显示，而无需文本。  当用户单击该按钮时，通常会更改外观。  
  
 典型的按钮是复选框、单选按钮和普通按钮。  `CButton` 对象可以根据 [按钮样式](../../mfc/reference/button-styles.md) 成为每个，指定在其对其 [创建](../Topic/CButton::Create.md) 成员函数。  
  
 另外，从 `CButton` 派生的 [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) 选件类支持按钮控件的创建标记使用位图图像代替文本。  `CBitmapButton` 可能包含按钮的，滚动，居中并禁用状态的单独位图。  
  
 您可以创建一个按钮控件从对话框模板或直接在代码。  在这两种情况下，首次调用构造函数 `CButton` 构造 `CButton` 对象;然后调用 **Create** 成员函数创建Windows按钮控件并将其附加到 `CButton` 对象。  
  
 构造。`CButton`从派生的类可以选件一步过程。  编写该派生类的构造函数和调用 **Create** 从构造函数内部。  
  
 如果希望处理Windows按钮控件发送的通知消息到其父\(通常从 [CDialog](../../mfc/reference/cdialog-class.md)派生的选件类\)中，添加一个消息映射项和消息处理程序成员函数为每个消息的父选件类。  
  
 每个消息映射项采用以下形式:  
  
 **ON\_**通知**\(**`id`，`memberFxn`**\)**  
  
 其中 `id` 指定将控件的子窗口ID通知和 `memberFxn` 是您处理编写通知父成员函数的名称。  
  
 父的函数原型如下所示:  
  
 **afx\_msg** `void` `memberFxn` **\( \);**  
  
 潜在的消息映射项如下所示:  
  
|映射项|发送父，在…|  
|---------|------------|  
|**ON\_BN\_CLICKED**|用户单击按钮。|  
|**ON\_BN\_DOUBLECLICKED**|用户双击按钮。|  
  
 如果您创建从对话框资源的一 `CButton` 对象，自动销毁 `CButton` 对象，当用户关闭对话框时。  
  
 如果在中创建的一 `CButton` 对象，则可能需要销毁它。  使用 **new** 功能，如果要创建在堆的 `CButton` 对象，则必须对对象的 **delete** 销毁它，在用户关闭Windows按钮控件。  如果在堆栈上创建 `CButton` 对象，或它在父对话框对象嵌入，自动销毁它。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CButton`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CBitmapButton Class](../../mfc/reference/cbitmapbutton-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)