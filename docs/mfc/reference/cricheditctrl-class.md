---
title: "CRichEditCtrl Class | Microsoft Docs"
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
  - "CRichEditCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCtrl class"
  - "CRichEditCtrl class, 公共控件"
  - "formatted text [C++]"
ms.assetid: 2be52788-822c-4c27-aafd-2471231e74eb
caps.latest.revision: 26
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRichEditCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供功能rich edit控件。  
  
## 语法  
  
```  
class CRichEditCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CRichEditCtrl::CRichEditCtrl](../Topic/CRichEditCtrl::CRichEditCtrl.md)|构造 `CRichEditCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRichEditCtrl::CanPaste](../Topic/CRichEditCtrl::CanPaste.md)|确定剪贴板的内容是否能粘贴到此rich edit控件。|  
|[CRichEditCtrl::CanRedo](../Topic/CRichEditCtrl::CanRedo.md)|确定是否具有在控件的任何事件重做队列。|  
|[CRichEditCtrl::CanUndo](../Topic/CRichEditCtrl::CanUndo.md)|确定编辑操作是否可以取消。|  
|[CRichEditCtrl::CharFromPos](../Topic/CRichEditCtrl::CharFromPos.md)|在编辑控件的工作区的检索有关字符的信息最接近指定的点。|  
|[CRichEditCtrl::Clear](../Topic/CRichEditCtrl::Clear.md)|清除当前选定内容。|  
|[CRichEditCtrl::Copy](../Topic/CRichEditCtrl::Copy.md)|复制当前选择到剪贴板。|  
|[CRichEditCtrl::Create](../Topic/CRichEditCtrl::Create.md)|创建Windows rich edit控件并将其与此 `CRichEditCtrl` 对象。|  
|[CRichEditCtrl::CreateEx](../Topic/CRichEditCtrl::CreateEx.md)|创建Windows丰富使用指定的扩展的 Windows 样式的编辑控件并将其与此 `CRichEditCtrl` 对象。|  
|[CRichEditCtrl::Cut](../Topic/CRichEditCtrl::Cut.md)|剪切当前选择到剪贴板。|  
|[CRichEditCtrl::DisplayBand](../Topic/CRichEditCtrl::DisplayBand.md)|显示此 `CRichEditCtrl` 对象内容的各个部分。|  
|[CRichEditCtrl::EmptyUndoBuffer](../Topic/CRichEditCtrl::EmptyUndoBuffer.md)|重置（清除）此 `CRichEditCtrl` 对象取消标记。|  
|[CRichEditCtrl::FindText](../Topic/CRichEditCtrl::FindText.md)|找到此 `CRichEditCtrl` 对象内的文本。|  
|[CRichEditCtrl::FindWordBreak](../Topic/CRichEditCtrl::FindWordBreak.md)|在指定的字符位置之前查找下一个断词或检索有关字符的信息在该位置。|  
|[CRichEditCtrl::FormatRange](../Topic/CRichEditCtrl::FormatRange.md)|格式化文本的大小目标输出设备的。|  
|[CRichEditCtrl::GetCharPos](../Topic/CRichEditCtrl::GetCharPos.md)|确定特定字符的位置本 `CRichEditCtrl` 对象中。|  
|[CRichEditCtrl::GetDefaultCharFormat](../Topic/CRichEditCtrl::GetDefaultCharFormat.md)|检索此 `CRichEditCtrl` 对象的当前默认字符格式设置属性。|  
|[CRichEditCtrl::GetEventMask](../Topic/CRichEditCtrl::GetEventMask.md)|检索此 `CRichEditCtrl` 对象的事件掩码。|  
|[CRichEditCtrl::GetFirstVisibleLine](../Topic/CRichEditCtrl::GetFirstVisibleLine.md)|确定此 `CRichEditCtrl` 对象的最顶层的可见的行。|  
|[CRichEditCtrl::GetIRichEditOle](../Topic/CRichEditCtrl::GetIRichEditOle.md)|检索指向此丰富的 `IRichEditOle` 接口编辑控件。|  
|[CRichEditCtrl::GetLimitText](../Topic/CRichEditCtrl::GetLimitText.md)|获取在用户可以输入此 `CRichEditCtrl` 对象的数量的限制文本。|  
|[CRichEditCtrl::GetLine](../Topic/CRichEditCtrl::GetLine.md)|从此 `CRichEditCtrl` 对象检索文本行。|  
|[CRichEditCtrl::GetLineCount](../Topic/CRichEditCtrl::GetLineCount.md)|检索的行数本 `CRichEditCtrl` 对象的。|  
|[CRichEditCtrl::GetModify](../Topic/CRichEditCtrl::GetModify.md)|确定此 `CRichEditCtrl` 对象的内容是否已更改，因为次保存。|  
|[CRichEditCtrl::GetOptions](../Topic/CRichEditCtrl::GetOptions.md)|检索rich edit控件选项。|  
|[CRichEditCtrl::GetParaFormat](../Topic/CRichEditCtrl::GetParaFormat.md)|检索在当前选定的段落格式设置此属性 `CRichEditCtrl` 对象。|  
|[CRichEditCtrl::GetPunctuation](../Topic/CRichEditCtrl::GetPunctuation.md)|检索丰富的当前标点符号\)编辑控件。  此消息只能在操作系统的亚洲语言版本。|  
|[CRichEditCtrl::GetRect](../Topic/CRichEditCtrl::GetRect.md)|检索此 `CRichEditCtrl` 对象的格式矩形。|  
|[CRichEditCtrl::GetRedoName](../Topic/CRichEditCtrl::GetRedoName.md)|检索下一个操作的类型，如果有，在控件中重做队列。|  
|[CRichEditCtrl::GetSel](../Topic/CRichEditCtrl::GetSel.md)|获取当前选择的开始和结束位置本 `CRichEditCtrl` 对象。|  
|[CRichEditCtrl::GetSelectionCharFormat](../Topic/CRichEditCtrl::GetSelectionCharFormat.md)|检索在当前选定的字符格式属性本 `CRichEditCtrl` 对象。|  
|[CRichEditCtrl::GetSelectionType](../Topic/CRichEditCtrl::GetSelectionType.md)|检索内容的类型在当前选定的此 `CRichEditCtrl` 对象。|  
|[CRichEditCtrl::GetSelText](../Topic/CRichEditCtrl::GetSelText.md)|获取当前选择的文本此对象的 `CRichEditCtrl`|  
|[CRichEditCtrl::GetTextLength](../Topic/CRichEditCtrl::GetTextLength.md)|检索文本的长度，在字符，本 `CRichEditCtrl` 对象。  不包括终止null字符）。|  
|[CRichEditCtrl::GetTextLengthEx](../Topic/CRichEditCtrl::GetTextLengthEx.md)|检索字符数或在丰富的字节编辑视图。  接受标志列表指出确定文本的长度方法在丰富的编辑控件|  
|[CRichEditCtrl::GetTextMode](../Topic/CRichEditCtrl::GetTextMode.md)|检索当前文本模式和移除级别rich edit控件。|  
|[CRichEditCtrl::GetTextRange](../Topic/CRichEditCtrl::GetTextRange.md)|检索文本的指定的范围。|  
|[CRichEditCtrl::GetUndoName](../Topic/CRichEditCtrl::GetUndoName.md)|检索类型的下取消事件，因此，如果有的话）。|  
|[CRichEditCtrl::GetWordWrapMode](../Topic/CRichEditCtrl::GetWordWrapMode.md)|检索包装当前的单词，以及中断丰富的字符串选项编辑控件。  此消息只能在操作系统的亚洲语言版本。|  
|[CRichEditCtrl::HideSelection](../Topic/CRichEditCtrl::HideSelection.md)|显示或隐藏当前选择。|  
|[CRichEditCtrl::LimitText](../Topic/CRichEditCtrl::LimitText.md)|限制用户可以输入 `CRichEditCtrl` 对象的数量的文本。|  
|[CRichEditCtrl::LineFromChar](../Topic/CRichEditCtrl::LineFromChar.md)|确定哪行包含特定字符。|  
|[CRichEditCtrl::LineIndex](../Topic/CRichEditCtrl::LineIndex.md)|检索特定代码行的字符的索引本 `CRichEditCtrl` 对象的。|  
|[CRichEditCtrl::LineLength](../Topic/CRichEditCtrl::LineLength.md)|检索特定行的长度本 `CRichEditCtrl` 对象的。|  
|[CRichEditCtrl::LineScroll](../Topic/CRichEditCtrl::LineScroll.md)|移至此 `CRichEditCtrl` 对象的文本。|  
|[CRichEditCtrl::Paste](../Topic/CRichEditCtrl::Paste.md)|插入剪贴板的内容。此丰富中编辑控件。|  
|[CRichEditCtrl::PasteSpecial](../Topic/CRichEditCtrl::PasteSpecial.md)|插入剪贴板的内容。此丰富中编辑控件以指定的数据格式。|  
|[CRichEditCtrl::PosFromChar](../Topic/CRichEditCtrl::PosFromChar.md)|检索指定字符的工作区坐标在编辑控件中。|  
|[CRichEditCtrl::Redo](../Topic/CRichEditCtrl::Redo.md)|重做在控件中的下一个操作重做队列。|  
|[CRichEditCtrl::ReplaceSel](../Topic/CRichEditCtrl::ReplaceSel.md)|使用指定的文本替换此 `CRichEditCtrl` 对象的当前选择。|  
|[CRichEditCtrl::RequestResize](../Topic/CRichEditCtrl::RequestResize.md)|强制执行此 `CRichEditCtrl` 对象发送请求调整通知。|  
|[CRichEditCtrl::SetAutoURLDetect](../Topic/CRichEditCtrl::SetAutoURLDetect.md)|指示URL自动检测是否有一个rich edit控件。|  
|[CRichEditCtrl::SetBackgroundColor](../Topic/CRichEditCtrl::SetBackgroundColor.md)|设置此 `CRichEditCtrl` 对象的背景色。|  
|[CRichEditCtrl::SetDefaultCharFormat](../Topic/CRichEditCtrl::SetDefaultCharFormat.md)|设置此 `CRichEditCtrl` 对象的当前默认字符格式设置属性。|  
|[CRichEditCtrl::SetEventMask](../Topic/CRichEditCtrl::SetEventMask.md)|将此 `CRichEditCtrl` 对象的事件掩码。|  
|[CRichEditCtrl::SetModify](../Topic/CRichEditCtrl::SetModify.md)|设置或清除此 `CRichEditCtrl` 对象的修改标志。|  
|[CRichEditCtrl::SetOLECallback](../Topic/CRichEditCtrl::SetOLECallback.md)|将此丰富的 `IRichEditOleCallback` COM对象编辑控件。|  
|[CRichEditCtrl::SetOptions](../Topic/CRichEditCtrl::SetOptions.md)|将此 `CRichEditCtrl` 对象的选项。|  
|[CRichEditCtrl::SetParaFormat](../Topic/CRichEditCtrl::SetParaFormat.md)|设置在当前选定的段落格式设置此属性 `CRichEditCtrl` 对象。|  
|[CRichEditCtrl::SetPunctuation](../Topic/CRichEditCtrl::SetPunctuation.md)|设置丰富的标点符号\)编辑控件。  此消息只能在操作系统的亚洲语言版本。|  
|[CRichEditCtrl::SetReadOnly](../Topic/CRichEditCtrl::SetReadOnly.md)|将此 `CRichEditCtrl` 对象的只读选项。|  
|[CRichEditCtrl::SetRect](../Topic/CRichEditCtrl::SetRect.md)|将此 `CRichEditCtrl` 对象的格式矩形。|  
|[CRichEditCtrl::SetSel](../Topic/CRichEditCtrl::SetSel.md)|设置此 `CRichEditCtrl` 对象的选择。|  
|[CRichEditCtrl::SetSelectionCharFormat](../Topic/CRichEditCtrl::SetSelectionCharFormat.md)|设置在当前选定的字符格式属性本 `CRichEditCtrl` 对象。|  
|[CRichEditCtrl::SetTargetDevice](../Topic/CRichEditCtrl::SetTargetDevice.md)|将此 `CRichEditCtrl` 对象的目标输出设备。|  
|[CRichEditCtrl::SetTextMode](../Topic/CRichEditCtrl::SetTextMode.md)|设置文本模式或移除级别rich edit控件。  如果控件包含文本，消息失败。|  
|[CRichEditCtrl::SetUndoLimit](../Topic/CRichEditCtrl::SetUndoLimit.md)|将取消队列中存储活动的最大数目。|  
|[CRichEditCtrl::SetWordCharFormat](../Topic/CRichEditCtrl::SetWordCharFormat.md)|将当前单词的字符格式属性本 `CRichEditCtrl` 对象。|  
|[CRichEditCtrl::SetWordWrapMode](../Topic/CRichEditCtrl::SetWordWrapMode.md)|设置自动换行，而Word中断丰富的选项编辑控件。  此消息只能在操作系统的亚洲语言版本。|  
|[CRichEditCtrl::StopGroupTyping](../Topic/CRichEditCtrl::StopGroupTyping.md)|从集合中其他类型的事件来停止该控件添加到当前取消事件。  控件将下一类型的事件，如果有，则到取消队列的新事件中。|  
|[CRichEditCtrl::StreamIn](../Topic/CRichEditCtrl::StreamIn.md)|插入输入流文本到此 `CRichEditCtrl` 对象。|  
|[CRichEditCtrl::StreamOut](../Topic/CRichEditCtrl::StreamOut.md)|存储在此 `CRichEditCtrl` 对象文本到输出流。|  
|[CRichEditCtrl::Undo](../Topic/CRichEditCtrl::Undo.md)|反转最后一个编辑操作。|  
  
## 备注  
 “rich edit控件”是用户可以输入和编辑文本的窗口。  该文本分配字符和段落格式设置，并且可以包含嵌入OLE对象。  rich edit控件为格式化文本的编程接口。  但是，应用程序必须实现必要所有用户界面的组件具有格式设置操作提供给用户。  
  
 此Windows公共控件\(并 `CRichEditCtrl` 选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  `CRichEditCtrl` 选件类支持2.0版，而3.0 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] rich edit控件。  
  
> [!CAUTION]
>  如果使用丰富在对话框中的编辑控件\(不管应用程序是否是SDI，MDI或基于对话框\)，必须调用 [AfxInitRichEdit](../Topic/AfxInitRichEdit.md)，在对话框中显示之前。  调用此函数的典型排列在程序的 `InitInstance` 成员函数。  您不需要调用它，每当您显示对话框，仅首次的。  如果使用 `CRichEditView`，您不必调用 `AfxInitRichEdit`。  
  
 有关使用 `CRichEditCtrl`的更多信息，请参见:  
  
-   [控件](../../mfc/controls-mfc.md)  
  
-   [使用CRichEditCtrl](../../mfc/using-cricheditctrl.md)  
  
-   知识库文章 Q259949：INFO: SetCaretPos\(\) 不合适与 CEdit 或 CRichEditCtrl 控件  
  
 对于使用基于丰富在MFC应用程序的编辑控件，请参见 [WORDPAD](../../top/visual-cpp-samples.md) 示例应用程序。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CRichEditCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [MFC示例WORDPAD](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)