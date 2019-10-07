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
ms.openlocfilehash: 8b407c6e832dde7a5865146e7cc12d1840d3234a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685860"
---
# <a name="destroying-the-dialog-box"></a>销毁对话框

模式对话框通常在堆栈帧上创建，并在创建它们的函数结束时销毁。 当对象超出范围时，将调用对话框对象的析构函数。

无模式对话框通常由父视图或框架窗口（应用程序的主框架窗口或文档框架窗口）创建和拥有。 默认[OnClose](../mfc/reference/cwnd-class.md#onclose)处理程序调用[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)，这会销毁对话框窗口。 如果此对话框单独出现，没有指向它的指针或其他特殊所有权语义，则应重写[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)以销毁C++对话框对象。 还应重写[OnCancel](../mfc/reference/cdialog-class.md#oncancel)并从它的内部调用 `DestroyWindow`。 否则，对话框的所有者应在不再需要时销毁C++对象。

## <a name="see-also"></a>请参阅

[使用 MFC 中的对话框](../mfc/life-cycle-of-a-dialog-box.md)
