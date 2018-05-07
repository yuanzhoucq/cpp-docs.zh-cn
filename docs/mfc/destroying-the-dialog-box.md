---
title: 销毁对话框 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66a3ef9a72107ffb36a75834a6e197aba394c420
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="destroying-the-dialog-box"></a>销毁对话框
有模式对话框通常在堆栈帧上创建和销毁创建它们在函数结束时。 当对象超出范围时，调用对话框对象的析构函数。  
  
 通常情况下创建和拥有父视图或框架窗口的无模式对话框-应用程序的主框架窗口或文档框架窗口。 默认值[OnClose](../mfc/reference/cwnd-class.md#onclose)处理程序调用[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)，这会被销毁对话框窗口。 如果单独出现时，使用它或其他特殊所有权语义不指向代表对话框中，则应重写[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)销毁 c + + 对话框对象。 你还应重写[OnCancel](../mfc/reference/cdialog-class.md#oncancel)并调用`DestroyWindow`从在其中。 否则，当不再需要时，对话框中的所有者应销毁 c + + 对象。  
  
## <a name="see-also"></a>请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

