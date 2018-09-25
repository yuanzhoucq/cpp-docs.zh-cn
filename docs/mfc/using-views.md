---
title: 使用视图 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interacting with users and role of view class [MFC]
- drawing [MFC], data
- rendering data
- view classes [MFC], role in managing user interaction
- CView class [MFC], view architecture
- MFC, views
- views [MFC], using
- painting data
- user input [MFC], interpreting through view class [MFC]
- view classes [MFC], role in displaying application data
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcf4af038617cce8326a3e63ba9b4ea66c277f66
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442092"
---
# <a name="using-views"></a>使用视图

该视图的职责是可以以图形方式向用户显示文档的数据还可以接受并将用户输入解释为对文档的操作。 你在编写视图类的任务是：

- 编写您的视图类的[OnDraw](../mfc/reference/cview-class.md#ondraw)成员函数，它将呈现文档的数据。

- 将相应的 Windows 消息和如菜单项的用户界面对象连接到的 view 类中的消息处理程序成员函数。

- 实现这些处理程序来解释用户输入。

此外，您可能需要重写其他`CView`派生的视图类中的成员函数。 具体而言，你可能想要重写[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)视图中执行特殊的初始化和[OnUpdate](../mfc/reference/cview-class.md#onupdate)以执行所需视图重绘自己之前的任何特殊处理。 对于多页文档，则还必须重写[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)来初始化具有要打印的页面和其他信息的数量的打印对话框。 有关详细信息重写`CView`成员函数，请参阅类[CView](../mfc/reference/cview-class.md)中*MFC 参考*。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [MFC 中可用的派生的视图类](../mfc/derived-view-classes-available-in-mfc.md)

- [在视图中绘制](../mfc/drawing-in-a-view.md)

- [通过视图解释用户输入](../mfc/interpreting-user-input-through-a-view.md)

- [视图在打印中的角色](../mfc/role-of-the-view-in-printing.md)

- [滚动和缩放视图](../mfc/scrolling-and-scaling-views.md)

- [初始化和清理文档和视图](../mfc/initializing-and-cleaning-up-documents-and-views.md)

## <a name="see-also"></a>请参阅

[文档/视图体系结构](../mfc/document-view-architecture.md)<br/>
[CFormView 类](../mfc/reference/cformview-class.md)<br/>
[记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)<br/>
[跳过序列化机制](../mfc/bypassing-the-serialization-mechanism.md)

