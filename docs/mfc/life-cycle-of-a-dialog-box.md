---
title: "对话框的生命周期 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 743aed312008d1908701933ec642dd52b0ac3ec8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="life-cycle-of-a-dialog-box"></a>对话框的生命周期
对话框中的生命周期，用户调用该对话框、 通常内的命令处理程序创建并初始化的对话框对象，在用户交互的对话框中，和关闭该对话框。  
  
 对于模式对话框，您的处理程序中收集用户输入后关闭该对话框任何数据。 由于对话框对象存在后其对话框窗口已关闭，你只需使用对话框类的成员变量来提取数据。  
  
 为无模式对话框，通常可能从对话框对象中提取数据仍会显示对话框时了。 在某些时候，销毁对话框对象;当发生这种情况取决于你的代码。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [创建并显示对话框](../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [创建模式对话框](../mfc/creating-modal-dialog-boxes.md)  
  
-   [创建无模式对话框](../mfc/creating-modeless-dialog-boxes.md)  
  
-   [在内存中使用的对话框模板](../mfc/using-a-dialog-template-in-memory.md)  
  
-   [设置对话框的背景色](../mfc/setting-the-dialog-boxs-background-color.md)  
  
-   [初始化对话框](../mfc/initializing-the-dialog-box.md)  
  
-   [处理您对话框中的 Windows 消息](../mfc/handling-windows-messages-in-your-dialog-box.md)  
  
-   [从对话框对象检索数据](../mfc/retrieving-data-from-the-dialog-object.md)  
  
-   [关闭对话框](../mfc/closing-the-dialog-box.md)  
  
-   [销毁对话框](../mfc/destroying-the-dialog-box.md)  
  
-   [对话框数据交换 (DDX) 和验证 (DDV)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [属性表对话框](../mfc/property-sheets-and-property-pages-mfc.md)  
  
## <a name="see-also"></a>请参阅  
 [对话框](../mfc/dialog-boxes.md)

