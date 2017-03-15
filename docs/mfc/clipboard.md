---
title: "剪贴板 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "剪贴板"
  - "剪贴板, 编程"
  - "复制数据"
  - "剪切和复制数据"
  - "传输数据"
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 剪贴板
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持的 MFC 应用程序此系列文章介绍如何实现 Windows 剪贴板。  Windows 剪贴板用于两种方法：  
  
-   实现标准"编辑"菜单命令，如剪切，复制，然后粘贴。  
  
-   实现具有 OLE 拖放 \(统一\) 的数据传输。  
  
 剪贴板是转移数据标准 Windows 方法在源和目标之间建立的。  也可能是很有用在 OLE 操作。  随着 OLE 的显示，在两个窗口中的剪贴板机制。  标准 Windows 剪贴板 API 可用，但是，它用 OLE 数据传输机制添加。  OLE 统一数据传输 \(UDT\) 支持剪切、复制、粘贴和与剪贴板和拖放。  
  
 剪贴板是整个 Windows 会话共享系统服务，因此，它没有句柄或自己的级别。  通过 [CWnd](../mfc/reference/cwnd-class.md)剪贴板管理类的成员函数。  
  
## 您想进一步了解什么？  
  
-   [剪贴板：何时使用每一剪贴板机制](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)  
  
-   [使用传统 Windows 剪贴板 API](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
-   [复制和粘贴数据](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [添加其他格式](../mfc/clipboard-adding-other-formats.md)  
  
-   [\<caps:sentence id\="tgt18" sentenceid\="1bc8aafd7da110d0b343b54cffa169d9" class\="tgtSentence"\>Windows 剪贴板\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms648709)  
  
-   [实现拖放和拖放 \(OLE\)](../mfc/drag-and-drop-ole.md)  
  
## 请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)