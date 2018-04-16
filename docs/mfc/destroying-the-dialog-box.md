---
title: "销毁对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b1b6c94c4c7efe3bc3300d6c8c5c34fbe890fb4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="destroying-the-dialog-box"></a>销毁对话框
有模式对话框通常在堆栈帧上创建和销毁创建它们在函数结束时。 当对象超出范围时，调用对话框对象的析构函数。  
  
 通常情况下创建和拥有父视图或框架窗口的无模式对话框-应用程序的主框架窗口或文档框架窗口。 默认值[OnClose](../mfc/reference/cwnd-class.md#onclose)处理程序调用[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)，这会被销毁对话框窗口。 如果单独出现时，使用它或其他特殊所有权语义不指向代表对话框中，则应重写[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)销毁 c + + 对话框对象。 你还应重写[OnCancel](../mfc/reference/cdialog-class.md#oncancel)并调用`DestroyWindow`从在其中。 否则，当不再需要时，对话框中的所有者应销毁 c + + 对象。  
  
## <a name="see-also"></a>请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

