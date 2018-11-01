---
title: 模式和无模式对话框
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 7e1dc9c40f60dc46117ee0673a038d5a63df7680
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528357"
---
# <a name="modal-and-modeless-dialog-boxes"></a>模式和无模式对话框

可以使用类[CDialog](../mfc/reference/cdialog-class.md)来管理两种类型的对话框：

- *模式对话框*，此操作需要用户响应后再继续执行程序

- *无模式对话框*，这均可在任何时间使用屏幕上都只允许用户执行其他活动

资源编辑和创建对话框模板的过程是相同的模式和无模式对话框。

创建您的程序的对话框需要执行以下步骤：

1. 使用[对话框编辑器](../windows/dialog-editor.md)设计对话框并创建其对话框模板资源。

1. 创建对话框类。

1. 连接[向消息处理程序的对话框资源控件](../windows/adding-event-handlers-for-dialog-box-controls.md)对话框类中。

1. 添加数据成员关联的对话框的控件，并指定[对话框数据交换](../mfc/dialog-data-exchange.md)并[对话框数据验证](../mfc/dialog-data-validation.md)的控件。

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

