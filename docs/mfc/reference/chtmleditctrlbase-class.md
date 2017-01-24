---
title: "CHtmlEditCtrlBase Class | Microsoft Docs"
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
  - "CHtmlEditCtrlBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHtmlEditCtrlBase class"
ms.assetid: e0cc74b4-8320-4570-b673-16c03d2ae266
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHtmlEditCtrlBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示编辑器元素的HTML。  
  
## 语法  
  
```  
  
template < class   
T  
 > class CHtmlEditCtrlBase  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CHtmlEditCtrlBase::AddToGlyphTable](../Topic/CHtmlEditCtrlBase::AddToGlyphTable.md)|将项添加到标志符号表，在设计模式下指定图像为特定标记显示。|  
|[CHtmlEditCtrlBase::Bold](../Topic/CHtmlEditCtrlBase::Bold.md)|切换所选文本的加粗状态。|  
|[CHtmlEditCtrlBase::Button](../Topic/CHtmlEditCtrlBase::Button.md)|复盖在当前选择的按钮控件。|  
|[CHtmlEditCtrlBase::CheckBox](../Topic/CHtmlEditCtrlBase::CheckBox.md)|复盖在当前选择的复选框控件。|  
|[CHtmlEditCtrlBase::ClearSelection](../Topic/CHtmlEditCtrlBase::ClearSelection.md)|清除当前选定内容。|  
|[CHtmlEditCtrlBase::Copy](../Topic/CHtmlEditCtrlBase::Copy.md)|复制当前选择到剪贴板。|  
|[CHtmlEditCtrlBase::Cut](../Topic/CHtmlEditCtrlBase::Cut.md)|复制当前选择到剪贴板然后删除它。|  
|[CHtmlEditCtrlBase::Delete](../Topic/CHtmlEditCtrlBase::Delete.md)|删除当前选择。|  
|[CHtmlEditCtrlBase::DropDownBox](../Topic/CHtmlEditCtrlBase::DropDownBox.md)|复盖在当前选定的一个下拉式选择控件。|  
|[CHtmlEditCtrlBase::EmptyGlyphTable](../Topic/CHtmlEditCtrlBase::EmptyGlyphTable.md)|从标志符号表中移除所有项，在设计模式隐藏为标记显示的任何图像。|  
|[CHtmlEditCtrlBase::ExecCommand](../Topic/CHtmlEditCtrlBase::ExecCommand.md)|执行命令。|  
|[CHtmlEditCtrlBase::Font](../Topic/CHtmlEditCtrlBase::Font.md)|打开"字体"对话框允许用户更改当前选择的文本颜色、字体和字号。|  
|[CHtmlEditCtrlBase::GetAbsolutePosition](../Topic/CHtmlEditCtrlBase::GetAbsolutePosition.md)|返回元素的placement属性是否为“绝对”。|  
|[CHtmlEditCtrlBase::GetBackColor](../Topic/CHtmlEditCtrlBase::GetBackColor.md)|检索当前选择的背景色。|  
|[CHtmlEditCtrlBase::GetBlockFormat](../Topic/CHtmlEditCtrlBase::GetBlockFormat.md)|检索当前个布局标记。|  
|[CHtmlEditCtrlBase::GetBlockFormatNames](../Topic/CHtmlEditCtrlBase::GetBlockFormatNames.md)|检索字符串以提供相应的布局标记。|  
|[CHtmlEditCtrlBase::GetBookMark](../Topic/CHtmlEditCtrlBase::GetBookMark.md)|检索书签定位的名称。|  
|[CHtmlEditCtrlBase::GetDocument](../Topic/CHtmlEditCtrlBase::GetDocument.md)|检索文档对象。|  
|[CHtmlEditCtrlBase::GetDocumentHTML](../Topic/CHtmlEditCtrlBase::GetDocumentHTML.md)|检索当前文档的HTML。|  
|[CHtmlEditCtrlBase::GetDocumentTitle](../Topic/CHtmlEditCtrlBase::GetDocumentTitle.md)|检索文档的标题。|  
|[CHtmlEditCtrlBase::GetEvent](../Topic/CHtmlEditCtrlBase::GetEvent.md)|检索接口指针。包含信息与新事件相关的事件对象。|  
|[CHtmlEditCtrlBase::GetEventSrcElement](../Topic/CHtmlEditCtrlBase::GetEventSrcElement.md)|检索激发该事件的对象。|  
|[CHtmlEditCtrlBase::GetFontFace](../Topic/CHtmlEditCtrlBase::GetFontFace.md)|检索字体名当前选择。|  
|[CHtmlEditCtrlBase::GetFontSize](../Topic/CHtmlEditCtrlBase::GetFontSize.md)|检索当前选择的字体大小。|  
|[CHtmlEditCtrlBase::GetForeColor](../Topic/CHtmlEditCtrlBase::GetForeColor.md)|检索当前选择的前景\(文本\)颜色。|  
|[CHtmlEditCtrlBase::GetFrameZone](../Topic/CHtmlEditCtrlBase::GetFrameZone.md)|返回当前页的安全区域在该浏览器的。|  
|[CHtmlEditCtrlBase::GetIsDirty](../Topic/CHtmlEditCtrlBase::GetIsDirty.md)|指示HTML文档是否已更改。|  
|[CHtmlEditCtrlBase::GetShowAlignedSiteTags](../Topic/CHtmlEditCtrlBase::GetShowAlignedSiteTags.md)|返回标志符号是否为具有 **styleFloat** 特性的所有元素显示。|  
|[CHtmlEditCtrlBase::GetShowAllTags](../Topic/CHtmlEditCtrlBase::GetShowAllTags.md)|返回浏览器是否在文档显示标志符号显示所有标记位置。|  
|[CHtmlEditCtrlBase::GetShowAreaTags](../Topic/CHtmlEditCtrlBase::GetShowAreaTags.md)|检索浏览器是否显示区域标记的标志符号。|  
|[CHtmlEditCtrlBase::GetShowBRTags](../Topic/CHtmlEditCtrlBase::GetShowBRTags.md)|检索浏览器是否显示乘法比标记的标志符号。|  
|[CHtmlEditCtrlBase::GetShowCommentTags](../Topic/CHtmlEditCtrlBase::GetShowCommentTags.md)|检索浏览器是否显示注释标记的标志符号。|  
|[CHtmlEditCtrlBase::GetShowMiscTags](../Topic/CHtmlEditCtrlBase::GetShowMiscTags.md)|检索浏览器是否显示在Microsoft Internet Explorer公开的所有标记4.0。|  
|[CHtmlEditCtrlBase::GetShowScriptTags](../Topic/CHtmlEditCtrlBase::GetShowScriptTags.md)|检索浏览器是否显示所有脚本标记的标志符号。|  
|[CHtmlEditCtrlBase::GetShowStyleTags](../Topic/CHtmlEditCtrlBase::GetShowStyleTags.md)|检索浏览器是否显示所有样式标记的标志符号。|  
|[CHtmlEditCtrlBase::GetShowUnknownTags](../Topic/CHtmlEditCtrlBase::GetShowUnknownTags.md)|检索浏览器是否显示所有未知标记的标志符号。|  
|[CHtmlEditCtrlBase::HorizontalLine](../Topic/CHtmlEditCtrlBase::HorizontalLine.md)|复盖在当前选定内容的一条水平线。|  
|[CHtmlEditCtrlBase::HyperLink](../Topic/CHtmlEditCtrlBase::HyperLink.md)|插入到当前选择的超链接。|  
|[CHtmlEditCtrlBase::IE50Paste](../Topic/CHtmlEditCtrlBase::IE50Paste.md)|执行兼容粘贴操作与Microsoft Internet Explorer 5。|  
|[CHtmlEditCtrlBase::Iframe](../Topic/CHtmlEditCtrlBase::Iframe.md)|复盖在当前选择的内联帧。|  
|[CHtmlEditCtrlBase::Image](../Topic/CHtmlEditCtrlBase::Image.md)|复盖在当前选择的图像。|  
|[CHtmlEditCtrlBase::Indent](../Topic/CHtmlEditCtrlBase::Indent.md)|由一个缩进增量递增选定文本的缩进。|  
|[CHtmlEditCtrlBase::InsFieldSet](../Topic/CHtmlEditCtrlBase::InsFieldSet.md)|复盖在当前选定的一个框。|  
|[CHtmlEditCtrlBase::InsInputButton](../Topic/CHtmlEditCtrlBase::InsInputButton.md)|复盖在当前选择的按钮控件。|  
|[CHtmlEditCtrlBase::InsInputHidden](../Topic/CHtmlEditCtrlBase::InsInputHidden.md)|插入到当前选择的隐藏控件。|  
|[CHtmlEditCtrlBase::InsInputImage](../Topic/CHtmlEditCtrlBase::InsInputImage.md)|复盖在当前选择的图像控件。|  
|[CHtmlEditCtrlBase::InsInputPassword](../Topic/CHtmlEditCtrlBase::InsInputPassword.md)|复盖在当前选择的加密控件。|  
|[CHtmlEditCtrlBase::InsInputReset](../Topic/CHtmlEditCtrlBase::InsInputReset.md)|复盖在当前选择的重置控件。|  
|[CHtmlEditCtrlBase::InsInputSubmit](../Topic/CHtmlEditCtrlBase::InsInputSubmit.md)|复盖在当前选定的一个提交控件。|  
|[CHtmlEditCtrlBase::InsInputUpload](../Topic/CHtmlEditCtrlBase::InsInputUpload.md)|复盖在当前选定的一个文件上载控件。|  
|[CHtmlEditCtrlBase::Is1DElement](../Topic/CHtmlEditCtrlBase::Is1DElement.md)|确定元素是否静态确定。|  
|[CHtmlEditCtrlBase::Is2DElement](../Topic/CHtmlEditCtrlBase::Is2DElement.md)|确定元素是否绝对定位。|  
|[CHtmlEditCtrlBase::Italic](../Topic/CHtmlEditCtrlBase::Italic.md)|切换在斜体和nonitalic之间的当前选择。|  
|[CHtmlEditCtrlBase::JustifyCenter](../Topic/CHtmlEditCtrlBase::JustifyCenter.md)|在哪些集中布局块找到当前选择。|  
|[CHtmlEditCtrlBase::JustifyLeft](../Topic/CHtmlEditCtrlBase::JustifyLeft.md)|在的左对齐布局块找到当前选择。|  
|[CHtmlEditCtrlBase::JustifyRight](../Topic/CHtmlEditCtrlBase::JustifyRight.md)|在哪些正确对齐布局块找到当前选择。|  
|[CHtmlEditCtrlBase::ListBox](../Topic/CHtmlEditCtrlBase::ListBox.md)|复盖在当前选择的列表框选择控件。|  
|[CHtmlEditCtrlBase::Marquee](../Topic/CHtmlEditCtrlBase::Marquee.md)|复盖在当前选定的一个空字幕。|  
|[CHtmlEditCtrlBase::NewDocument](../Topic/CHtmlEditCtrlBase::NewDocument.md)|创建新文档。|  
|[CHtmlEditCtrlBase::OrderList](../Topic/CHtmlEditCtrlBase::OrderList.md)|切换之间的当前选择的有序列表，并以普通布局块。|  
|[CHtmlEditCtrlBase::Outdent](../Topic/CHtmlEditCtrlBase::Outdent.md)|该格式缩进中的一个渐进式要求降低哪些块找到当前选择。|  
|[CHtmlEditCtrlBase::Paragraph](../Topic/CHtmlEditCtrlBase::Paragraph.md)|复盖在当前选定的一个分行符|  
|[CHtmlEditCtrlBase::Paste](../Topic/CHtmlEditCtrlBase::Paste.md)|复盖剪贴板的内容在当前选定内容的。|  
|[CHtmlEditCtrlBase::PrintDocument](../Topic/CHtmlEditCtrlBase::PrintDocument.md)|打印当前文件。|  
|[CHtmlEditCtrlBase::PrintPreview](../Topic/CHtmlEditCtrlBase::PrintPreview.md)|使用默认打印预览模板或自定义模板，打开的打印预览窗口当前文件。|  
|[CHtmlEditCtrlBase::QueryStatus](../Topic/CHtmlEditCtrlBase::QueryStatus.md)|调用此方法查询命令的状态。|  
|[CHtmlEditCtrlBase::RadioButton](../Topic/CHtmlEditCtrlBase::RadioButton.md)|复盖在当前选择的无线控件。|  
|[CHtmlEditCtrlBase::RefreshDocument](../Topic/CHtmlEditCtrlBase::RefreshDocument.md)|刷新当前文件。|  
|[CHtmlEditCtrlBase::RemoveFormat](../Topic/CHtmlEditCtrlBase::RemoveFormat.md)|从当前选定内容中移除格式标记。|  
|[CHtmlEditCtrlBase::SaveAs](../Topic/CHtmlEditCtrlBase::SaveAs.md)|保存当前网页到文件。|  
|[CHtmlEditCtrlBase::SelectAll](../Topic/CHtmlEditCtrlBase::SelectAll.md)|选择整个文档。|  
|[CHtmlEditCtrlBase::Set2DPosition](../Topic/CHtmlEditCtrlBase::Set2DPosition.md)|允许绝对定位的元素将移动。|  
|[CHtmlEditCtrlBase::SetAbsolutePosition](../Topic/CHtmlEditCtrlBase::SetAbsolutePosition.md)|将元素的位置属性“绝对”或“静态”。|  
|[CHtmlEditCtrlBase::SetAtomicSelection](../Topic/CHtmlEditCtrlBase::SetAtomicSelection.md)|设置基本选择模式。|  
|[CHtmlEditCtrlBase::SetAutoURLDetectMode](../Topic/CHtmlEditCtrlBase::SetAutoURLDetectMode.md)|打开和关闭自动检测URL。|  
|[CHtmlEditCtrlBase::SetBackColor](../Topic/CHtmlEditCtrlBase::SetBackColor.md)|将当前选择的背景色。|  
|[CHtmlEditCtrlBase::SetBlockFormat](../Topic/CHtmlEditCtrlBase::SetBlockFormat.md)|设置当前个布局标记。|  
|[CHtmlEditCtrlBase::SetBookMark](../Topic/CHtmlEditCtrlBase::SetBookMark.md)|创建当前选择的一个书签定位点或插入点。|  
|[CHtmlEditCtrlBase::SetCSSEditingLevel](../Topic/CHtmlEditCtrlBase::SetCSSEditingLevel.md)|选择\(级CSS的CSS1或CSS2\)编辑器将支持，因此，如果有的话）。|  
|[CHtmlEditCtrlBase::SetDefaultComposeSettings](../Topic/CHtmlEditCtrlBase::SetDefaultComposeSettings.md)|调用此方法将组成默认设置。|  
|[CHtmlEditCtrlBase::SetDesignMode](../Topic/CHtmlEditCtrlBase::SetDesignMode.md)|设置的设计模式。|  
|[CHtmlEditCtrlBase::SetDisableEditFocusUI](../Topic/CHtmlEditCtrlBase::SetDisableEditFocusUI.md)|在编辑器中具有焦点的元素时禁用阴影边框和处理。|  
|[CHtmlEditCtrlBase::SetDocumentHTML](../Topic/CHtmlEditCtrlBase::SetDocumentHTML.md)|设置当前文档的HTML。|  
|[CHtmlEditCtrlBase::SetFontFace](../Topic/CHtmlEditCtrlBase::SetFontFace.md)|将当前选定的字体。|  
|[CHtmlEditCtrlBase::SetFontSize](../Topic/CHtmlEditCtrlBase::SetFontSize.md)|将当前选定的字体大小。|  
|[CHtmlEditCtrlBase::SetForeColor](../Topic/CHtmlEditCtrlBase::SetForeColor.md)|将当前选择的前景\(文本\)颜色。|  
|[CHtmlEditCtrlBase::SetIE5PasteMode](../Topic/CHtmlEditCtrlBase::SetIE5PasteMode.md)|设置粘贴操作与Microsoft Internet Explorer 5兼容。|  
|[CHtmlEditCtrlBase::SetLiveResize](../Topic/CHtmlEditCtrlBase::SetLiveResize.md)|使浏览器在调整或移动操作过程中持续更新元素的外观。|  
|[CHtmlEditCtrlBase::SetMultiSelect](../Topic/CHtmlEditCtrlBase::SetMultiSelect.md)|启用多重选择。|  
|[CHtmlEditCtrlBase::SetOverrideCursor](../Topic/CHtmlEditCtrlBase::SetOverrideCursor.md)|从命令浏览器更改鼠标指针。|  
|[CHtmlEditCtrlBase::SetOverwriteMode](../Topic/CHtmlEditCtrlBase::SetOverwriteMode.md)|切换在插入之间的文本输入模式并复盖。|  
|[CHtmlEditCtrlBase::SetRespectVisInDesign](../Topic/CHtmlEditCtrlBase::SetRespectVisInDesign.md)|在设计模式隐藏不可见的元素。|  
|[CHtmlEditCtrlBase::SetShowAlignedSiteTags](../Topic/CHtmlEditCtrlBase::SetShowAlignedSiteTags.md)|显示具有一个 **styleFloat** 特性的所有元素的标志符号。|  
|[CHtmlEditCtrlBase::SetShowAllTags](../Topic/CHtmlEditCtrlBase::SetShowAllTags.md)|在文档显示标志符号显示所有标记位置。|  
|[CHtmlEditCtrlBase::SetShowAreaTags](../Topic/CHtmlEditCtrlBase::SetShowAreaTags.md)|显示所有区域标记的标志符号。|  
|[CHtmlEditCtrlBase::SetShowBRTags](../Topic/CHtmlEditCtrlBase::SetShowBRTags.md)|显示所有乘法比标记的标志符号。|  
|[CHtmlEditCtrlBase::SetShowCommentTags](../Topic/CHtmlEditCtrlBase::SetShowCommentTags.md)|显示所有注释标记的标志符号。|  
|[CHtmlEditCtrlBase::SetShowMiscTags](../Topic/CHtmlEditCtrlBase::SetShowMiscTags.md)|显示Microsoft Internet Explorer公开的所有标记4.0。|  
|[CHtmlEditCtrlBase::SetShowScriptTags](../Topic/CHtmlEditCtrlBase::SetShowScriptTags.md)|显示所有脚本标记的标志符号。|  
|[CHtmlEditCtrlBase::SetShowStyleTags](../Topic/CHtmlEditCtrlBase::SetShowStyleTags.md)|显示所有样式标记的标志符号。|  
|[CHtmlEditCtrlBase::SetShowUnknownTags](../Topic/CHtmlEditCtrlBase::SetShowUnknownTags.md)|显示所有未知标记的标志符号。|  
|[CHtmlEditCtrlBase::TextArea](../Topic/CHtmlEditCtrlBase::TextArea.md)|复盖在当前选定的一个多行文本输入控件。|  
|[CHtmlEditCtrlBase::TextBox](../Topic/CHtmlEditCtrlBase::TextBox.md)|复盖在当前选择的文本控件。|  
|[CHtmlEditCtrlBase::UnBookmark](../Topic/CHtmlEditCtrlBase::UnBookmark.md)|从当前选定内容中移除所有书签。|  
|[CHtmlEditCtrlBase::Underline](../Topic/CHtmlEditCtrlBase::Underline.md)|切换在下划线和不带下划线之间的当前选择。|  
|[CHtmlEditCtrlBase::Unlink](../Topic/CHtmlEditCtrlBase::Unlink.md)|从当前选定内容中移除所有超链接。|  
|[CHtmlEditCtrlBase::UnorderList](../Topic/CHtmlEditCtrlBase::UnorderList.md)|切换之间的当前选择的有序列表，并以普通布局块。|  
  
#### 参数  
 `T`  
 派生类的名称。  
  
## 备注  
 **CHtmlEditCtrlBase** 用于编辑命令，如 [粗体](../Topic/CHtmlEditCtrlBase::Bold.md)浏览器的HTML提供成员函数。  （或者，可以调用 [ExecCommand](../Topic/CHtmlEditCtrlBase::ExecCommand.md) 执行 **IDM\_BOLD** 命令。）  
  
 **CHtmlEditCtrlBase** 不打算自己的重要。  它旨在是显示编辑浏览器功能的HTML的派生类的基类\(请参见 [CHtmlEditCtrl](../../mfc/reference/chtmleditctrl-class.md) 和 [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)）。  
  
## 继承层次结构  
 `CHtmlEditCtrlBase`  
  
## 要求  
 **Header:** afxhtml.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [HTMLEdit示例](../../top/visual-cpp-samples.md)