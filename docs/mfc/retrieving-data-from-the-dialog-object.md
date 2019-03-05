---
title: 从对话框对象检索数据
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], retrieving user data
- dialog box data [MFC]
- data [MFC], retrieving
- GetDlgItemText method [MFC]
- SetDlgItemText method [MFC]
- SetWindowText method [MFC]
- dialog box data [MFC], retrieving
- retrieving data [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- dialog box controls [MFC], initializing values
- DDX (dialog data exchange) [MFC]
- MFC dialog boxes [MFC], retrieving user input
- data retrieval [MFC], dialog boxes
- data [MFC], dialog boxes
- DDX (dialog data exchange) [MFC], about DDX
- DDX (dialog data exchange) [MFC], retrieving data from Dialog object
- GetWindowText method [MFC]
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
ms.openlocfilehash: b376edc3ee7d8abbca43da6d823e71abad99bc5d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279024"
---
# <a name="retrieving-data-from-the-dialog-object"></a>从对话框对象检索数据

该框架提供的简单方法来初始化对话框中的控件的值和从控件检索值。 更费力的手动方法是调用函数，例如`SetDlgItemText`并`GetDlgItemText`类的成员函数`CWnd`，这不适用于控制 windows。 使用这些函数，您访问每个控件分别来设置或获取它的值，如调用函数`SetWindowText`和`GetWindowText`。 框架的方法会自动初始化并检索。

对话框数据交换 (DDX) 可让你更轻松地交换数据之间的对话框对象中的对话框框和成员变量中的控件。 此交换适用于这两种方式。 若要初始化的控件在对话框中，可以在对话框对象中设置数据成员的值和框架将这些值传输给控件之前显示的对话框。 然后可以在任何时候更新对话框数据成员的用户输入的数据。 此时，您可以使用数据： 数据成员变量引用。

您还可以安排对话框控件与对话框数据验证 (DDV) 自动进行验证的值。

中更详细地介绍 DDX 和 DDV[对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。

对于模式对话框，可以检索用户输入时的任何数据`DoModal`返回 IDOK 但对话框之前在销毁对象。 对于无模式对话框，您可以从检索数据的对话框对象在任何时候通过调用`UpdateData`使用参数**TRUE** ，然后访问对话框类成员变量。 中更详细地讨论了此主题[对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。

## <a name="see-also"></a>请参阅

[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)
