---
title: 如何执行默认打印
ms.date: 11/04/2016
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
ms.openlocfilehash: 5019bcad769c4b7cdb699facef145a21d9b5e11c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508419"
---
# <a name="how-default-printing-is-done"></a>如何执行默认打印

本文介绍 Windows 中与 MFC 框架有关的默认打印过程。

在 MFC 应用程序中，视图类具有名为 `OnDraw` 的成员函数，其包含所有绘图代码。 `OnDraw`采用作为参数的[CDC](../mfc/reference/cdc-class.md)对象的指针。 `CDC` 对象表示用于接收 `OnDraw` 所生成图像的设备上下文。 当显示文档的窗口收到[WM_PAINT](/windows/win32/gdi/wm-paint)消息时, 框架将调用`OnDraw`并向其传递屏幕 ( [CPaintDC](../mfc/reference/cpaintdc-class.md)对象) 的设备上下文。 因此，`OnDraw` 的输出将显示在屏幕上。

在面向 Windows 的编程中，将输出发送到打印机非常类似于将输出发送到屏幕。 这是因为 Windows 图形设备接口 (GDI) 与硬件无关。 通过使用适当的设备上下文，您可使用相同的 GDI 函数进行屏幕显示或打印。 如果 `CDC` 对象收到表示打印机的 `OnDraw`，则 `OnDraw` 的输出将发送到打印机。

这介绍 MFC 应用程序如何执行简单打印，而不需要您的额外工作。 框架负责显示“打印”对话框和为打印机创建设备上下文。 当用户从“文件”菜单中选择“打印”命令后，视图会将此设备上下文传递到在打印机上绘制文档的 `OnDraw`。

但是，打印与屏幕显示之间有一些重要差异。 打印时，您必须将文档分到不同的页并每次显示一页，而不是在窗口中显示任何可见部分。 按照推论，您必须了解纸张的大小（它是信纸大小、合法大小还是信封）。 您可能需要按不同的方向（如横向模式或纵向模式）打印。 Microsoft 基础类库无法预测您的应用程序将如何处理这些问题，因此它将提供一个协议供您添加这些功能。

这一文章中介绍了[多页文档](../mfc/multipage-documents.md)。

## <a name="see-also"></a>请参阅

[打印](../mfc/printing.md)
