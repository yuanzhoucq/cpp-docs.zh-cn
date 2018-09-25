---
title: 对话框的生命周期 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05138040b6283b7af01f6e010bc371490aea495e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440493"
---
# <a name="life-cycle-of-a-dialog-box"></a>对话框的生命周期

在对话框中的生命周期，在用户调用对话框中，通常内的命令处理程序创建并初始化对话框对象，用户与进行交互对话框中，并关闭该对话框。

对于模式对话框，您的处理程序收集用户输入后关闭该对话框的任何数据。 由于对话框对象存在于其对话框窗口已关闭后，您只需使用自己的对话框类的成员变量来提取数据。

为无模式对话框，通常可能从对话框对象中提取数据对话框的仍可见时了。 在某些时候，销毁对话框对象;当发生这种情况取决于你的代码。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [创建并显示对话框](../mfc/creating-and-displaying-dialog-boxes.md)

- [创建模式对话框](../mfc/creating-modal-dialog-boxes.md)

- [创建无模式对话框](../mfc/creating-modeless-dialog-boxes.md)

- [在内存中使用对话框模板](../mfc/using-a-dialog-template-in-memory.md)

- [设置对话框的背景色](../mfc/setting-the-dialog-boxs-background-color.md)

- [初始化对话框](../mfc/initializing-the-dialog-box.md)

- [处理您对话框中的 Windows 消息](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [从对话框对象检索数据](../mfc/retrieving-data-from-the-dialog-object.md)

- [关闭对话框](../mfc/closing-the-dialog-box.md)

- [销毁对话框](../mfc/destroying-the-dialog-box.md)

- [对话框数据交换 (DDX) 和验证 (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [属性表对话框](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)

