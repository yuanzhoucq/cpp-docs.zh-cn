---
title: "剪贴板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 304f20f94880b0bd8cb671788c5c06b69d25d377
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard"></a>剪贴板
此系列文章介绍如何在 MFC 应用程序中实现对 Windows 剪贴板的支持。 两种方式使用 Windows 剪贴板：  
  
-   实现标准编辑菜单命令，例如剪切、 复制和粘贴。  
  
-   实现统一数据传输使用拖动拖放 (OLE)。  
  
 剪贴板是一个源和目标之间传输数据的标准 Windows 方法。 它还可在 OLE 操作中非常有用。 使用 OLE 的问世，有两种剪贴板机制在 Windows 中。 标准 Windows 剪贴板 API 仍然可用，但具有已附有 OLE 数据传输机制。 OLE 统一数据传输 (UDT) 支持剪切、 复制和粘贴剪贴板和拖放。  
  
 剪贴板是共享由整个 Windows 会话，因此它没有的句柄或自己的类的系统服务。 你管理的类成员函数通过剪贴板[CWnd](../mfc/reference/cwnd-class.md)。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [何时使用每一剪贴板机制](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)  
  
-   [使用传统的 Windows 剪贴板 API](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
-   [复制和粘贴数据](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [添加其他格式](../mfc/clipboard-adding-other-formats.md)  
  
-   [Windows 剪贴板](https://msdn.microsoft.com/library/ms648709)  
  
-   [实现拖放 (OLE)](../mfc/drag-and-drop-ole.md)  
  
## <a name="see-also"></a>请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)
