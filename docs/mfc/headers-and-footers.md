---
title: 页眉和页脚
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
ms.openlocfilehash: 7024c57dbe41a579582d409d0536db0ca0bc46d6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620105"
---
# <a name="headers-and-footers"></a>页眉和页脚

本文说明如何将页眉和页脚添加到打印文档。

当您在屏幕上查看文档时，文档的名称和您在文档中的当前位置通常显示在标题栏和状态栏中。 在查看文档的打印副本时，在页眉或页脚显示名称和页码很有用。 这是一种常用方法，采用此方法后，甚至是“所见即所得”程序执行打印和屏幕显示的方式都不同。

[OnPrint](reference/cview-class.md#onprint)成员函数是打印页眉或页脚的适当位置，因为它是为每个页面调用的，并且因为它仅用于打印，而不是用于屏幕显示。 您可以定义单独的函数来打印页眉或页脚，并从 `OnPrint` 将其传入打印机设备上下文。 你可能需要在调用[OnDraw](reference/cview-class.md#ondraw)之前调整窗口原点或范围，以避免页面正文与页眉或页脚重叠。 您可能还必须修改 `OnDraw`，因为页容纳的文档的数量的可能减少。

补偿页眉或页脚所采用区域的一种方法是使用[CPrintInfo](reference/cprintinfo-structure.md)的**m_rectDraw**成员。 每打印一页，就会使用该页的可用区域初始化此成员。 如果在打印页的正文之前打印页眉或页脚，则可以减小存储在**m_rectDraw**中的矩形的大小，以考虑页眉或页脚拍摄的区域。 然后， `OnPrint` 可以参考**m_rectDraw**来找出打印页面正文所需的区域。

你不能从[OnPrepareDC](reference/cview-class.md#onpreparedc)打印页眉或其他任何内容，因为它是在 `StartPage` 调用[CDC](reference/cdc-class.md)的成员函数之前调用的。 此时，打印机设备上下文被视为位于页边界上。 您只能从 `OnPrint` 成员函数执行打印。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [打印多页文档](multipage-documents.md)

- [分配用于打印的 GDI 资源](allocating-gdi-resources.md)

## <a name="see-also"></a>另请参阅

[打印](printing.md)
