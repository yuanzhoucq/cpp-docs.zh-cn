---
title: 对话栏
ms.date: 11/19/2018
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
ms.openlocfilehash: 052e0b8a085c052f73d3c6540521f57fdfbb9c51
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624889"
---
# <a name="dialog-bars"></a>对话栏

对话栏是一个工具栏，这是一种可以包含任何类型的控件的[控件条](control-bars.md)。 由于它具有无模式对话框的特性，因此[CDialogBar](reference/cdialogbar-class.md)对象提供了一个功能更强大的工具栏。

工具栏和 `CDialogBar` 对象之间有一些主要差异。 `CDialogBar` 对象是从可以借助 Visual C++ 对话框编辑器创建的、可包含各种 Windows 控件的对话框模板资源创建的。 用户可以在控件之间进行切换。 您可以指定对齐样式，以将对话栏与父框架窗口的任何部分对齐，甚至可以在调整父窗口大小时将其留在原来的位置。 下图演示了带有各种控件的对话栏。

![VC 对话栏](../mfc/media/vc378t1.gif "VC 对话栏") <br/>
对话栏

在其他方面，使用 `CDialogBar` 对象与使用无模式对话框类似。 使用对话框编辑器来设计和创建对话框资源。

对话栏的优点之一是，它们可以包括除按钮之外的控件。

虽然从 `CDialog` 派生您自己的对话框类很正常，但您通常不会为对话栏派生您自己的类。 对话栏是主窗口的扩展，任何对话框控件通知消息（如**BN_CLICKED**或**EN_CHANGE**）都将发送到对话栏（主窗口）的父窗口。

## <a name="see-also"></a>另请参阅

[用户界面元素](user-interface-elements-mfc.md)<br/>
[示例](../overview/visual-cpp-samples.md)
