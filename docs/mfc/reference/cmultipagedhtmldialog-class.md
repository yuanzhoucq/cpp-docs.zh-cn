---
title: "CMultiPageDHtmlDialog Class | Microsoft Docs"
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
  - "CMultiPageDHtmlDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiPageDHtmlDialog class"
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMultiPageDHtmlDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一个多页"对话框按顺序显示多个HTML页和处理来自每页的事件。  
  
## 语法  
  
```  
class CMultiPageDHtmlDialog : public CDHtmlDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](../Topic/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog.md)|构造一个多页\(向导样式\) DHTML对话框对象。|  
|[CMultiPageDHtmlDialog::~CMultiPageDHtmlDialog](../Topic/CMultiPageDHtmlDialog::~CMultiPageDHtmlDialog.md)|销毁一个多页DHTML对话框对象。|  
  
## 备注  
 执行此操作的结构是 [DHTML和URL事件映射](http://msdn.microsoft.com/zh-cn/2a7332f0-79d7-46e4-b816-0a618c46777a)，包含每页的 [嵌入事件映射](../Topic/BEGIN_EMBED_DHTML_EVENT_MAP.md)。  
  
## 示例  
 此多页"对话框假定定义简单的类似向导的功能的三个HTML资源。  第一页具有 `Next` 按钮，第二 **Prev** 和 `Next` 按钮和第三 **Prev** 按钮。  当某个按钮时，事件处理程序函数调用 [CDHtmlDialog::LoadFromResource](../Topic/CDHtmlDialog::LoadFromResource.md) 将相应的新页。  
  
 选件类声明的相关部分\(在CMyMultiPageDlg.h\):  
  
 [!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/CPP/cmultipagedhtmldialog-class_1.h)]  
  
 选件类实现的相关部分\(在CMyMultipageDlg.cpp\):  
  
 [!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/CPP/cmultipagedhtmldialog-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)  
  
 `CMultiPageDHtmlDialog`  
  
## 要求  
 **Header:** afxdhtml.h  
  
## 请参阅  
 [CDHtmlDialog Class](../../mfc/reference/cdhtmldialog-class.md)   
 [Multipage DHTML and URL Event Maps \(NIB\)](http://msdn.microsoft.com/zh-cn/2a7332f0-79d7-46e4-b816-0a618c46777a)