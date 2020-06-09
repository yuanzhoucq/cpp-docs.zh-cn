---
title: 文档-视图体系结构的纵向
ms.date: 11/04/2016
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
ms.openlocfilehash: f0e71c42004b5409eeb6f5e2ddabd33296cf5f49
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623452"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>文档/视图结构的纵览

文档和视图在典型的 MFC 应用程序中是成对的。 数据存储在文档中，但视图具有对数据的特别访问权。 将文档与视图分离也会将数据的存储和维护与数据的显示分离。

## <a name="gaining-access-to-document-data-from-the-view"></a>获取从视图访问文档数据的权限

视图使用[GetDocument](reference/cview-class.md#getdocument)函数访问其文档的数据，该函数返回指向文档的指针，或使视图类成为文档类的 c + + `friend` 。 视图随后会在准备好绘制或以其他方式操作数据时使用其访问权限获取数据。

例如，从视图的[OnDraw](reference/cview-class.md#ondraw)成员函数中，视图用于 `GetDocument` 获取文档指针。 然后，它使用该指针访问文档中的 `CString` 数据成员。 视图将字符串传递到 `TextOut` 函数。 若要查看此示例的代码，请参阅[视图中的绘图](drawing-in-a-view.md)。

## <a name="user-input-to-the-view"></a>对视图的用户输入

视图还可能在自身中将鼠标单击解释为数据的选择或编辑。 同样，它也可能将键击解释为数据输入或编辑。 假设用户在管理文本的视图中输入了一个字符串。 视图获取指向文档的指针并使用该指针将新数据传递到文档，从而将数据存储在某个数据结构中。

## <a name="updating-multiple-views-of-the-same-document"></a>更新同一文档的多个视图

在具有同一文档的多个视图（如文本编辑器中的拆分窗口）的应用程序中，视图首先将新数据传递到文档。 然后，它会调用文档的[UpdateAllViews](reference/cdocument-class.md#updateallviews)成员函数，该函数会告知文档的所有视图自行更新，并反映新的数据。 这将同步视图。

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [文档/视图体系结构的优点](advantages-of-the-document-view-architecture.md)

- [文档/视图体系结构的替代项](alternatives-to-the-document-view-architecture.md)

## <a name="see-also"></a>另请参阅

[文档/视图体系结构](document-view-architecture.md)
