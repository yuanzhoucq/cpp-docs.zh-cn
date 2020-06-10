---
title: 打印
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: 3d2ef494be66171cbcbf2b8b9e19c29c8bdc5c2f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619807"
---
# <a name="printing"></a>打印

Microsoft Windows 实现与设备无关的显示。 在 MFC 中，这意味着，同一绘图调用在 `OnDraw` 视图类的成员函数中，负责在显示器和其他设备（如打印机）上进行绘制。 对于打印预览，目标设备是显示的模拟打印机输出。

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>你在打印中的角色与框架的角色

您的视图类具有以下职责：

- 通知框架文档中有多少页。

- 当系统请求打印指定页面时，请绘制文档的该部分。

- 分配和释放打印所需的任何字体或其他图形设备接口（GDI）资源。

- 如有必要，在打印给定页面之前发送更改打印机模式所需的任何转义代码，例如，在每页上更改打印方向。

框架的职责如下：

- 显示 "**打印**" 对话框。

- 为打印机创建[CDC](reference/cdc-class.md)对象。

- 调用对象的[StartDoc](reference/cdc-class.md#startdoc)和[EndDoc](reference/cdc-class.md#enddoc)成员函数 `CDC` 。

- 重复调用对象的[StartPage](reference/cdc-class.md#startpage)成员函数 `CDC` ，通知视图类应打印哪个页面，并调用该对象的[EndPage](reference/cdc-class.md#endpage)成员函数 `CDC` 。

- 在适当的时间调用视图中的可重写函数。

以下文章介绍了框架如何支持打印和打印预览：

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [如何完成默认打印](how-default-printing-is-done.md)

- [多页文档](multipage-documents.md)

- [页眉和页脚](headers-and-footers.md)

- [分配用于打印的 GDI 资源](allocating-gdi-resources.md)

- [打印预览](print-preview-architecture.md)

## <a name="see-also"></a>另请参阅

[打印和打印预览](printing-and-print-preview.md)
