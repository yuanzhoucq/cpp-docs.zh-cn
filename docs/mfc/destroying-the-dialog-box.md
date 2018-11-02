---
title: 销毁对话框
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
ms.openlocfilehash: f84e36a2a002610c294653012c40707fddcaba54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607462"
---
# <a name="destroying-the-dialog-box"></a>销毁对话框

通常在堆栈帧上创建和销毁创建它们在函数结束时的模式对话框。 当对象超出范围时，调用对话框对象的析构函数。

通常情况下创建和拥有父视图或框架窗口的无模式对话框，应用程序的主框架窗口或文档框架窗口。 默认值[OnClose](../mfc/reference/cwnd-class.md#onclose)处理程序调用[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)，其中销毁对话框窗口。 如果对话框的是相互独立，与任何指向它或其他特殊的所有权语义的则应重写[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)要销毁的 c + + 对话框对象。 您还应该重写[OnCancel](../mfc/reference/cdialog-class.md#oncancel) ，并调用`DestroyWindow`从在其中。 否则，当不再需要时，对话框的所有者应销毁 c + + 对象。

## <a name="see-also"></a>请参阅

[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

