---
title: 打印
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: a46096592c9983d04d2122bfabb56ece9346c4bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371194"
---
# <a name="printing"></a>打印

微软视窗实现与设备无关的显示。 在 MFC 中，这意味着视图类`OnDraw`的成员函数中的相同绘图调用负责在显示器和其他设备（如打印机）上进行绘图。 对于打印预览，目标设备是打印到显示器的模拟打印机输出。

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>您在打印中的角色与框架的角色

您的视图类具有以下职责：

- 通知框架文档中有多少页。

- 当要求打印指定的页面时，绘制文档的该部分。

- 分配和取消分配打印所需的任何字体或其他图形设备接口 （GDI） 资源。

- 如有必要，在打印给定页面之前发送更改打印机模式所需的任何转义代码，例如，以每页更改打印方向。

该框架的职责如下：

- 显示 **"打印"** 对话框。

- 为打印机创建[CDC](../mfc/reference/cdc-class.md)对象。

- 调用`CDC`对象的[StartDoc](../mfc/reference/cdc-class.md#startdoc)和[EndDoc](../mfc/reference/cdc-class.md#enddoc)成员函数。

- `CDC`重复调用对象的[StartPage](../mfc/reference/cdc-class.md#startpage)成员函数，通知应打印哪个页面的视图类，并调用`CDC`对象的[EndPage](../mfc/reference/cdc-class.md#endpage)成员函数。

- 在适当的时间调用视图中的可重写函数。

以下文章讨论框架如何支持打印和打印预览：

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [如何完成默认打印](../mfc/how-default-printing-is-done.md)

- [多页文档](../mfc/multipage-documents.md)

- [标题和页脚](../mfc/headers-and-footers.md)

- [分配用于打印的 GDI 资源](../mfc/allocating-gdi-resources.md)

- [打印预览](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>另请参阅

[打印和打印预览](../mfc/printing-and-print-preview.md)
