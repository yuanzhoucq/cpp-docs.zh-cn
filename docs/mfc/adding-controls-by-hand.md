---
title: 手动添加控件
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
ms.openlocfilehash: cf665247dd1ef24bb71d160097fa9514ff8be147
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589380"
---
# <a name="adding-controls-by-hand"></a>手动添加控件

你可以[将控件添加到对话框中，使用对话框编辑器](../mfc/using-the-dialog-editor-to-add-controls.md)或将它们添加你自己，使用代码。

若要自行创建控件对象，通常将嵌入在 c + + 对话框中，c + + 控件对象或框架窗口对象。 类似于 framework 中的许多其他对象，控件需要两阶段构造。 应调用控件的**创建**成员函数作为创建父对话框的框或框架窗口的一部分。 对于对话框，这通常是[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，和的框架窗口中[OnCreate](../mfc/reference/cwnd-class.md#oncreate)。

下面的示例演示如何声明`CEdit`对象中派生的对话框类的类声明，然后调用`Create`成员函数在`OnInitDialog`。 因为`CEdit`对象声明为嵌入的对象，它会自动构建时构造对话框对象，但仍必须使用其自己初始化`Create`成员函数。

[!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]

以下`OnInitDialog`函数将设置一个矩形，然后调用`Create`创建 Windows 编辑控件并将其附加到未初始化`CEdit`对象。

[!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]

创建编辑对象后，您还可以设置输入的焦点到控件通过调用`SetFocus`成员函数。 最后，返回从 0`OnInitDialog`以显示将焦点设置。 如果返回非零值，对话框管理器会将焦点设置到对话框项列表中的第一个控件项。 在大多数情况下，你将想要使用对话框编辑器向对话框添加控件。

## <a name="see-also"></a>请参阅

[创建和使用控件](../mfc/making-and-using-controls.md)<br/>
[控件](../mfc/controls-mfc.md)<br/>
[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)

