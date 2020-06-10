---
title: 文档-视图体系结构的优点
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: 80f7141ec62d509defdea361586399bd375df0d1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623276"
---
# <a name="advantages-of-the-documentview-architecture"></a>文档/视图结构的优点

使用 MFC 文档/视图体系结构的主要优点是体系结构支持同一文档的多个视图。 （如果您不需要多个视图，并且应用程序的文档/视图的小开销很小，则可以避免这种体系结构。 [文档/视图体系结构的替代方法](alternatives-to-the-document-view-architecture.md)。）

假设您的应用程序允许用户以电子表格形式或以图表形式查看数值数据。 用户可能想要同时查看原始数据、电子表格窗体和数据产生的图表。 在单独的框架窗口或拆分器窗格中的单个窗口内显示这些单独的视图。 现在假设用户可以编辑电子表格中的数据，并查看图表中立即反映的更改。

在 MFC 中，电子表格视图和图表视图基于从 CView 派生的不同类。 这两个视图都将与单个文档对象相关联。 该文档存储数据（或可能从数据库获取数据）。 这两个视图都可以访问该文档并显示其从中检索的数据。

当用户更新其中一个视图时，该视图对象将调用 `CDocument::UpdateAllViews` 。 该函数通知所有文档的视图，每个视图都使用文档中的最新数据来更新自身。 对不同视图进行同步的单一调用 `UpdateAllViews` 。

这种情况很难在不将数据与视图分离的情况下进行编码，尤其是在视图存储数据本身的情况下。 文档/视图非常简单。 该框架为你执行大部分协调工作。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [文档/视图的替代项](alternatives-to-the-document-view-architecture.md)

- [CDocument](reference/cdocument-class.md)

- [CView](reference/cview-class.md)

- [CDocument：： UpdateAllViews](reference/cdocument-class.md#updateallviews)

- [CView：： GetDocument](reference/cview-class.md#getdocument)

## <a name="see-also"></a>另请参阅

[文档/视图体系结构](document-view-architecture.md)
