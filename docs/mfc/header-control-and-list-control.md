---
title: 标题控件和列表控件
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
ms.openlocfilehash: 53dd6f1a7878d82a7f7ac48dd7082d791323941b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370475"
---
# <a name="header-control-and-list-control"></a>标题控件和列表控件

在大多数情况下，您将使用嵌入在[CListCtrl](../mfc/reference/clistctrl-class.md)或[CListView](../mfc/reference/clistview-class.md)对象中的标头控件。 但是，在某些情况下，需要单独的标头控件对象，例如操作以列或行排列的数据，位于[CView](../mfc/reference/cview-class.md)派生的对象中。 在这些情况下，您需要更好地控制嵌入式标头控件的外观和默认行为。

在希望标头控件提供标准默认行为的常见情况下，您可能需要改用[CListCtrl](../mfc/reference/clistctrl-class.md)或[CListView。](../mfc/reference/clistview-class.md) 当`CListCtrl`您想要默认标头控件的功能时使用，该功能嵌入到列表视图公共控件中。 当您希望嵌入在视图对象中的默认标头控件的功能时，请使用[CListView。](../mfc/reference/clistview-class.md)

> [!NOTE]
> 仅当使用**LVS_REPORT**样式创建列表视图控件时，这些控件才包括内置标头控件。

在大多数情况下，可以通过更改包含列表视图控件的样式来修改嵌入标头控件的外观。 此外，还可以通过父列表视图控件的成员函数获取有关标头控件的信息。 但是，为了对嵌入标头控件的属性和样式进行完全控制和访问，建议获取指向标头控件对象的指针。

可以从任一`CListCtrl`或`CListView`调用相应类`GetHeaderCtrl`的成员函数访问嵌入的标头控制对象。 以下代码对此做了演示：

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [对标题控件使用图像列表](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>另请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
