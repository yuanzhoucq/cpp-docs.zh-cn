---
title: 对话框数据交换
ms.date: 11/19/2018
helpviewer_keywords:
- initializing dialog boxes
- canceling data exchange
- dialog box data, retrieving
- DDX (dialog data exchange), data exchange mechanism
- dialog boxes [MFC], initializing
- dialog boxes [MFC], retrieving user input using DDX
- dialog box data
- dialog boxes [MFC], data exchange
- CDataExchange class [MFC], using DDX
- DoDataExchange method [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- transferring dialog box data
- DDX (dialog data exchange), canceling
- UpdateData method [MFC]
- retrieving dialog box data [MFC]
ms.assetid: 4675f63b-41d2-45ed-b6c3-235ad8ab924b
ms.openlocfilehash: 9a0199577ea46520c2eadc308812de8a1ce4b514
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2019
ms.locfileid: "71685803"
---
# <a name="dialog-data-exchange"></a>对话框数据交换

如果使用 DDX 机制，则可设置对话框对象的成员变量的初始值（通常在 `OnInitDialog` 处理程序或对话框构造函数中）。 在对话框显示之前，框架的 DDX 机制会将成员变量的值传输到对话框中的控件，这些控件在对话框本身显示为响应 `DoModal` 或 `Create` 时出现。 `OnInitDialog` 中的 `CDialog` 的默认实现调用 `UpdateData` 类的 `CWnd` 成员函数以在对话框中初始化控件。

当用户单击 "确定" 按钮时，相同的机制将值从控件传输到成员变量中（或在调用参数**为 TRUE**的 `UpdateData` 成员函数时）。 对话框数据验证机制将验证为其指定了验证规则的所有数据项。

下图演示了对话框数据交换。

![对话框数据交换](../mfc/media/vc379d1.gif "对话框数据交换") <br/>
对话框数据交换

`UpdateData` 在两个方向上都是由传递给它的**BOOL**参数指定的。 若要执行交换，`UpdateData` 将设置 `CDataExchange` 对象并调用对话框类的 `CDialog` 的 `DoDataExchange` 成员函数的重写。 `DoDataExchange` 采用 `CDataExchange` 类型的参数。 传递给 `CDataExchange` 的 `UpdateData` 对象表示交换的上下文，并将此类信息定义交换的方向。

当你（或代码向导）重写 `DoDataExchange` 时，可以指定对每个数据成员（控件）调用一个 DDX 函数。 每个 DDX 函数都了解如何基于由 `CDataExchange` 传递给 `DoDataExchange` 的 `UpdateData` 自变量提供的上下文双向交换数据。

MFC 提供了许多用于不同类型交换的 DDX 函数。 以下示例演示了一个 `DoDataExchange` 重写，其中调用两个 DDX 函数和一个 DDV 函数：

[!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]

`DDX_` 和 `DDV_` 行是数据映射。 显示的示例 DDX 和 DDV 函数分别为复选框控件和编辑框控件。

如果用户取消了模式对话框，则 `OnCancel` 成员函数将终止对话框，`DoModal` 返回值**IDCANCEL**。 在这种情况下，对话框和对话框对象之间不交换数据。

## <a name="see-also"></a>请参阅

[对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)<br/>
[使用 MFC 中的对话框](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[对话框数据验证](../mfc/dialog-data-validation.md)
