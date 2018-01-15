---
title: "将 Windows 消息映射到您的类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4701b0ae9f71099febb1a239cea6285fb0a7b229
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-windows-messages-to-your-class"></a>将 Windows 消息映射到您的类
如果你需要处理 Windows 消息对话框中，重写适当的处理程序函数。 为此，请使用属性窗口[将消息映射](../mfc/reference/mapping-messages-to-functions.md)到对话框类。 这写入消息映射项为每个消息，并将消息处理程序成员函数添加到类。 使用 Visual c + + 源代码编辑器在消息处理程序中编写代码。  
  
 此外可以重写的成员函数[CDialog](../mfc/reference/cdialog-class.md)及其基类，尤其是[CWnd](../mfc/reference/cwnd-class.md)。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [消息处理和映射](../mfc/message-handling-and-mapping.md)  
  
-   [经常重写成员函数](../mfc/commonly-overridden-member-functions.md)  
  
-   [经常添加的成员函数](../mfc/commonly-added-member-functions.md)  
  
## <a name="see-also"></a>请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

