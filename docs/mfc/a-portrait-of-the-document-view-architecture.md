---
title: "文档视图体系结构的纵览 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ceadc55945a31e4787287beb6943897784aeaad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="a-portrait-of-the-documentview-architecture"></a>文档/视图结构的纵览
文档和视图在典型的 MFC 应用程序中是成对的。 数据存储在文档中，但视图具有对数据的特别访问权。 将文档与视图分离也会将数据的存储和维护与数据的显示分离。  
  
## <a name="gaining-access-to-document-data-from-the-view"></a>获取从视图访问文档数据的权限  
 视图访问其文档的数据使用[GetDocument](../mfc/reference/cview-class.md#getdocument)函数，返回一个指针，该文档，或通过使视图类 c + +`friend`的文档类。 视图随后会在准备好绘制或以其他方式操作数据时使用其访问权限获取数据。  
  
 例如，从该视图的[OnDraw](../mfc/reference/cview-class.md#ondraw)成员函数，该视图使用**GetDocument**获取文档指针。 然后，它使用该指针访问文档中的 `CString` 数据成员。 视图将字符串传递到 `TextOut` 函数。 若要查看此示例的代码，请参阅[在视图中绘制](../mfc/drawing-in-a-view.md)。  
  
## <a name="user-input-to-the-view"></a>对视图的用户输入  
 视图还可能在自身中将鼠标单击解释为数据的选择或编辑。 同样，它也可能将键击解释为数据输入或编辑。 假设用户在管理文本的视图中输入了一个字符串。 视图获取指向文档的指针并使用该指针将新数据传递到文档，从而将数据存储在某个数据结构中。  
  
## <a name="updating-multiple-views-of-the-same-document"></a>更新同一文档的多个视图  
 应用程序具有同一文档的多个视图中，文本编辑器中的拆分窗口如-视图首先将新数据传递到文档。 然后，它调用文档的[UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)成员函数，它指示要自行更新，以反映新的数据的文档的所有视图。 这将同步视图。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [文档/视图体系结构的优势](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [文档/视图体系结构的替代方法](../mfc/alternatives-to-the-document-view-architecture.md)  
  
## <a name="see-also"></a>请参阅  
 [文档/视图体系结构](../mfc/document-view-architecture.md)

