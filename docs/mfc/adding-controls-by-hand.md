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
ms.openlocfilehash: 4efd1c23c7e4d6f7d8e6fa9fe046f8de11c825a6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626537"
---
# <a name="adding-controls-by-hand"></a>手动添加控件

您可以[使用对话框编辑器将控件添加到对话框](using-the-dialog-editor-to-add-controls.md)，也可以使用代码自行添加控件。

若要自行创建控件对象，通常会在 c + + 对话框或框架窗口对象中嵌入 c + + 控件对象。 与框架中的许多其他对象一样，控件需要两阶段构造。 应在创建父对话框或框架窗口时调用控件的**Create**成员函数。 对于对话框，此操作通常在[OnInitDialog](reference/cdialog-class.md#oninitdialog)中完成，对于框架窗口，则在[OnCreate](reference/cwnd-class.md#oncreate)中完成。

下面的示例演示如何 `CEdit` 在派生对话框类的类声明中声明一个对象，然后 `Create` 在中调用该成员函数 `OnInitDialog` 。 由于 `CEdit` 对象被声明为嵌入的对象，因此在构造对话框对象时将自动构造该对象，但仍必须使用其自己的成员函数对其进行初始化 `Create` 。

[!code-cpp[NVC_MFCControlLadenDialog#1](codesnippet/cpp/adding-controls-by-hand_1.h)]

下面的 `OnInitDialog` 函数设置一个矩形，然后调用 `Create` 来创建 Windows 编辑控件，并将其附加到未初始化的 `CEdit` 对象。

[!code-cpp[NVC_MFCControlLadenDialog#2](codesnippet/cpp/adding-controls-by-hand_2.cpp)]

创建编辑对象后，还可以通过调用成员函数将输入焦点设置到控件 `SetFocus` 。 最后，从返回0， `OnInitDialog` 以显示设置了焦点。 如果返回非零值，对话框管理器会将焦点设置到对话框项列表中的第一个控件项。 在大多数情况下，你需要将控件添加到对话框，并在对话框编辑器中添加。

## <a name="see-also"></a>另请参阅

[创建和使用控件](making-and-using-controls.md)<br/>
[控件](controls-mfc.md)<br/>
[CDialog：： OnInitDialog](reference/cdialog-class.md#oninitdialog)
