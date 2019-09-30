---
title: 初始化对话框
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 14cdf94bef79f254b4aaa2c1c0dfba6c88b7498b
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685621"
---
# <a name="initializing-the-dialog-box"></a>初始化对话框

对话框及其所有控件创建完成后，在屏幕上显示对话框（在任一类型上）之后，将调用对话框对象的[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)成员函数。 对于模式对话框，这种情况在 `DoModal` 调用期间出现。 对于无模式对话框，在调用 `Create` 时调用 `OnInitDialog`。 您通常可重写 `OnInitDialog` 来初始化对话框的控件，如设置编辑框的初始文本。 您必须从 `OnInitDialog` 的重写中调用基类 `CDialog` 的 `OnInitDialog` 成员函数。

如果要设置对话框的背景色（以及应用程序中所有其他对话框的颜色），请参阅[设置对话框的背景色](../mfc/setting-the-dialog-boxs-background-color.md)。

## <a name="see-also"></a>请参阅

[使用 MFC 中的对话框](../mfc/life-cycle-of-a-dialog-box.md)
