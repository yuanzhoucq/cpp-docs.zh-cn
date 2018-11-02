---
title: 文档视图体系结构的优点
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: ccb2e786eb2397efd2d8b34e118f0935fdb05283
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655957"
---
# <a name="advantages-of-the-documentview-architecture"></a>文档/视图结构的优点

使用 MFC 文档/视图体系结构的主要优点是体系结构能够很好地支持在同一文档的多个视图。 （如果不需要多个视图和文档/视图的少量开销是在应用程序中过多，可以避免在体系结构。 [文档/视图体系结构的替代方法](../mfc/alternatives-to-the-document-view-architecture.md)。)

假设你的应用程序可让用户以电子表格形式或以图表形式查看数值数据。 用户可能想要查看同时这两个原始数据，在电子表格窗体和数据而得出的图表中。 在单独的框架窗口中或在同一个窗口内的拆分器窗格中显示这些单独的视图。 现在假设用户可以编辑电子表格和，请参阅中的数据所做的更改可立即反映在图表中。

在 MFC 中，会在不同的类派生自 CView 基于电子表格视图和图表视图。 这两个视图将与单个文档对象相关联。 文档存储的数据 （或可能是从数据库中获取它）。 这两个视图访问文档，并显示从它检索到的数据。

当用户更新的视图，查看对象调用之一`CDocument::UpdateAllViews`。 该函数会通知的所有文档的视图，并更新自身使用的最新数据进行文档，每个视图。 对单个调用`UpdateAllViews`同步的不同视图。

这种情况下很难代码而无需分离数据从视图中，尤其是当视图存储数据本身。 文档/视图中，很容易。 该框架为您完成大部分协调工作。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [替代方案，以文档/视图](../mfc/alternatives-to-the-document-view-architecture.md)

- [CDocument](../mfc/reference/cdocument-class.md)

- [CView](../mfc/reference/cview-class.md)

- [CDocument::UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)

- [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)

## <a name="see-also"></a>请参阅

[文档/视图体系结构](../mfc/document-view-architecture.md)

