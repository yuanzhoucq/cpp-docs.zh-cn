---
title: 模式和无模式对话框 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4f03d67e1eb9962f4303694db4850e800151404
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346556"
---
# <a name="modal-and-modeless-dialog-boxes"></a>模式和无模式对话框
你可以使用类[CDialog](../mfc/reference/cdialog-class.md)管理两种类型的对话框：  
  
-   *有模式对话框*，即要求用户响应后再继续执行程序  
  
-   *无模式对话框*，它位于屏幕和均可在任何时候使用，但允许其他用户活动  
  
 资源编辑和创建对话框模板的过程是相同的模式和无模式对话框。  
  
 创建你的程序的对话框需要执行下列步骤：  
  
1.  使用[对话框编辑器](../windows/dialog-editor.md)设计对话框并创建其对话框模板资源。  
  
2.  创建对话框类。  
  
3.  连接[消息处理程序的对话框资源控件](../windows/adding-event-handlers-for-dialog-box-controls.md)对话框类中。  
  
4.  添加数据成员与关联对话框的控件指定[对话框数据交换](../mfc/dialog-data-exchange.md)和[对话框数据验证](../mfc/dialog-data-validation.md)的控件。  
  
## <a name="see-also"></a>请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

