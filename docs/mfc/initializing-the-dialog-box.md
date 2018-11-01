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
ms.openlocfilehash: 2312a158835b28e7a17a6c30bb1fa148a63c07fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507960"
---
# <a name="initializing-the-dialog-box"></a>初始化对话框

在该对话框后框和它的所有控件都创建，但在对话框 （的任一类型） 的框出现在屏幕上，对话框对象的[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)调用成员函数。 对于模式对话框，这种情况在 `DoModal` 调用期间出现。 对于无模式对话框`OnInitDialog`时，将调用`Create`调用。 您通常可重写 `OnInitDialog` 来初始化对话框的控件，如设置编辑框的初始文本。 您必须从 `OnInitDialog` 的重写中调用基类 `CDialog` 的 `OnInitDialog` 成员函数。

如果你想要设置对话框的背景色 （和该应用程序中的所有其他对话框），请参阅[设置对话框的背景色](../mfc/setting-the-dialog-boxs-background-color.md)。

## <a name="see-also"></a>请参阅

[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

