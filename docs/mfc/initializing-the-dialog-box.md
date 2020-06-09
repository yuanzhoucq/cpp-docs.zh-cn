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
ms.openlocfilehash: 1f8f8f7e40b1c873c4428542c628d02e250f14b4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626342"
---
# <a name="initializing-the-dialog-box"></a>初始化对话框

对话框及其所有控件创建完成后，在屏幕上显示对话框（在任一类型上）之后，将调用对话框对象的[OnInitDialog](reference/cdialog-class.md#oninitdialog)成员函数。 对于模式对话框，这种情况在 `DoModal` 调用期间出现。 对于无模式对话框， `OnInitDialog` 在调用时调用 `Create` 。 您通常可重写 `OnInitDialog` 来初始化对话框的控件，如设置编辑框的初始文本。 您必须从 `OnInitDialog` 的重写中调用基类 `CDialog` 的 `OnInitDialog` 成员函数。

如果要设置对话框的背景色（以及应用程序中所有其他对话框的颜色），请参阅[设置对话框的背景色](setting-the-dialog-boxs-background-color.md)。

## <a name="see-also"></a>另请参阅

[在 MFC 中使用对话框](life-cycle-of-a-dialog-box.md)
