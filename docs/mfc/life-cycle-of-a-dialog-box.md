---
title: 使用 MFC 中的对话框
ms.date: 09/27/2019
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: ad15250cf9a8dd663072cf9423263260bbb40a0e
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685726"
---
# <a name="working-with-dialog-boxes-in-mfc"></a>使用 MFC 中的对话框

在对话框的生命周期内，用户调用对话框，通常在创建和初始化对话框对象的命令处理程序中，用户与对话框交互，然后对话框关闭。

对于模式对话框，处理程序将收集用户在对话框关闭后输入的任何数据。 由于对话框对象已关闭，因此您只需使用对话框类的成员变量来提取数据。

对于无模式对话框，您通常可以从对话框对象中提取数据，而对话框仍可见。 在某个时间点，对话框对象已销毁;发生这种情况时，具体取决于你的代码。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [创建和显示对话框](../mfc/creating-and-displaying-dialog-boxes.md)

- [创建模式对话框](../mfc/creating-modal-dialog-boxes.md)

- [创建无模式对话框](../mfc/creating-modeless-dialog-boxes.md)

- [在内存中使用对话框模板](../mfc/using-a-dialog-template-in-memory.md)

- [设置对话框的背景色](../mfc/setting-the-dialog-boxs-background-color.md)

- [初始化对话框](../mfc/initializing-the-dialog-box.md)

- [处理对话框中的 Windows 消息](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [从对话框对象检索数据](../mfc/retrieving-data-from-the-dialog-object.md)

- [关闭对话框](../mfc/closing-the-dialog-box.md)

- [销毁对话框](../mfc/destroying-the-dialog-box.md)

- [对话框数据交换（DDX）和验证（DDV）](../mfc/dialog-data-exchange-and-validation.md)

- [属性表对话框](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)
