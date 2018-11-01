---
title: 关闭对话框
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: fe57c5603f1b0e9ea0b6fb9e6ea8d80bec961f6e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448108"
---
# <a name="closing-the-dialog-box"></a>关闭对话框

当用户选择模式对话框中的某个按钮（通常是“确定”按钮或“取消”按钮）时，该对话框将关闭。 选择确定或取消按钮会导致 Windows 对话框对象发送**BN_CLICKED**与按钮控件通知消息的 ID，或者**IDOK**或**IDCANCEL**。 `CDialog` 提供了针对以下消息的默认处理程序函数：`OnOK` 和 `OnCancel`。 默认处理程序调用 `EndDialog` 成员函数以关闭对话框窗口。 你还可以从你自己的代码中调用 `EndDialog`。 有关详细信息，请参阅[EndDialog](../mfc/reference/cdialog-class.md#enddialog)类的成员函数`CDialog`中*MFC 参考*。

若要安排关闭和删除无模式对话框中，重写`PostNcDestroy`并调用**删除**运算符**这**指针。 [销毁对话框](../mfc/destroying-the-dialog-box.md)说明接下来发生的变化。

## <a name="see-also"></a>请参阅

[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

