---
title: "CFindReplaceDialog Class | Microsoft Docs"
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
  - "CFindReplaceDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFindReplaceDialog class"
  - "Find/Replace dialog box"
  - "替换文本"
  - "替换文本, CFindReplaceDialog class"
  - "文本搜索, CFindReplaceDialog class"
  - "文本搜索, 替换文本"
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
caps.latest.revision: 25
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFindReplaceDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以实现标准字符串"查找\/替换在应用程序的对话框。  
  
## 语法  
  
```  
class CFindReplaceDialog : public CCommonDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFindReplaceDialog::CFindReplaceDialog](../Topic/CFindReplaceDialog::CFindReplaceDialog.md)|调用此构造函数 `CFindReplaceDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFindReplaceDialog::Create](../Topic/CFindReplaceDialog::Create.md)|创建并显示一 `CFindReplaceDialog` 对话框。|  
|[CFindReplaceDialog::FindNext](../Topic/CFindReplaceDialog::FindNext.md)|调用此函数确定用户是否希望以查找字符串的下一个匹配项。|  
|[CFindReplaceDialog::GetFindString](../Topic/CFindReplaceDialog::GetFindString.md)|调用该函数检索当前查找字符串。|  
|[CFindReplaceDialog::GetNotifier](../Topic/CFindReplaceDialog::GetNotifier.md)|调用该函数检索在签入的消息处理程序的 **FINDREPLACE** 结构。|  
|[CFindReplaceDialog::GetReplaceString](../Topic/CFindReplaceDialog::GetReplaceString.md)|调用该函数检索当前替换字符串。|  
|[CFindReplaceDialog::IsTerminating](../Topic/CFindReplaceDialog::IsTerminating.md)|调用此函数确定对话框是停止。|  
|[CFindReplaceDialog::MatchCase](../Topic/CFindReplaceDialog::MatchCase.md)|调用此函数确定用户是否希望完全匹配搜索字符串的大小写。|  
|[CFindReplaceDialog::MatchWholeWord](../Topic/CFindReplaceDialog::MatchWholeWord.md)|调用此函数确定用户是否希望仅与整个运行。|  
|[CFindReplaceDialog::ReplaceAll](../Topic/CFindReplaceDialog::ReplaceAll.md)|调用此函数确定用户是否希望该字符串的所有匹配项替换。|  
|[CFindReplaceDialog::ReplaceCurrent](../Topic/CFindReplaceDialog::ReplaceCurrent.md)|调用此函数确定用户是否希望当前字替换。|  
|[CFindReplaceDialog::SearchDown](../Topic/CFindReplaceDialog::SearchDown.md)|调用此函数确定用户是否在向下希望继续搜索。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CFindReplaceDialog::m\_fr](../Topic/CFindReplaceDialog::m_fr.md)|用于的结构自定义 `CFindReplaceDialog` 对象。|  
  
## 备注  
 与其他Windows通用对话框，状态，并在屏幕上时，`CFindReplaceDialog` 对象是无模式，允许用户与其他窗口交互。  有两 `CFindReplaceDialog` 对象:查找对话框和"查找\/替换"对话框。  虽然对话框允许用户输入搜索，并搜索\/替换字符串，它们不执行任何一个搜索的或替换的功能。  必须将它们添加到应用程序。  
  
 若要构造 `CFindReplaceDialog` 对象，请使用没有参数\)的提供的构造函数\(。  因为这是无模式对话框中，使用 **new** 运算符，而不是堆栈的，请将在堆上的对象。  
  
 在 `CFindReplaceDialog` 对象构造完成，必须调用 [创建](../Topic/CFindReplaceDialog::Create.md) 成员函数创建和显示对话框。  
  
 使用 [m\_fr](../Topic/CFindReplaceDialog::m_fr.md) 框架在调用 **Create**之前初始化对话框。  `m_fr` 机制是类型 [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)。  有关此结构的更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 为了父窗口可以将通知查找\/替换请求，在该对帧的windows必须使用Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) 功能和使用 [ON\_REGISTERED\_MESSAGE](../Topic/ON_REGISTERED_MESSAGE.md) 消息映射宏处理此注册的消息。  
  
 可以确定用户是否确定终止具有 `IsTerminating` 成员函数的对话框。  
  
 `CFindReplaceDialog` 依赖于随Windows 3.1版和更高版本的COMMDLG.DLL文件。  
  
 若要自定义对话框，从 `CFindReplaceDialog`派生选件类，提供了一个自定义对话框模板，并将消息映射处理从扩展控件的通知消息。  应通过任何未处理的消息路由到基类。  
  
 挂钩函数不需要自定义。  
  
 有关使用 `CFindReplaceDialog`的更多信息，请参见 [用于通用对话框选件类](../../mfc/common-dialog-classes.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFindReplaceDialog`  
  
## 要求  
 **Header:** afxdlgs.h  
  
## 请参阅  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)