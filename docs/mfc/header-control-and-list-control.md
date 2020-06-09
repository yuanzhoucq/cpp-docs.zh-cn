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
ms.openlocfilehash: f9dd34b27ddbdc0b99fafbb23ad1cf9782d98605
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626423"
---
# <a name="header-control-and-list-control"></a>标题控件和列表控件

在大多数情况下，将使用嵌入到[CListCtrl](reference/clistctrl-class.md)或[CListView](reference/clistview-class.md)对象中的标头控件。 但是，在某些情况下，需要单独的标头控件对象，例如在[CView](reference/cview-class.md)派生的对象中操作数据、按列或行排列。 在这些情况下，您需要更好地控制嵌入标头控件的外观和默认行为。

如果希望标题控件提供标准的默认行为，则可能要改为使用[CListCtrl](reference/clistctrl-class.md)或[CListView](reference/clistview-class.md) 。 `CListCtrl`希望在列表视图公共控件中嵌入默认标头控件的功能时使用。 若要在视图对象中嵌入默认标头控件的功能，请使用[CListView](reference/clistview-class.md) 。

> [!NOTE]
> 如果列表视图控件是使用**LVS_REPORT**样式创建的，则这些控件仅包含内置标头控件。

在大多数情况下，可以通过更改包含列表视图控件的样式来修改嵌入的标头控件的外观。 此外，可以通过父列表视图控件的成员函数获取有关标头控件的信息。 但是，若要对嵌入的标头控件的特性和样式进行完全控制和访问，建议获取指向标头控件对象的指针。

可以通过 `CListCtrl` `CListView` 调用相应类的成员函数，从或访问嵌入的标头控件对象 `GetHeaderCtrl` 。 以下代码对此做了演示：

[!code-cpp[NVC_MFCControlLadenDialog#14](codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [对标题控件使用图像列表](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>另请参阅

[使用 CHeaderCtrl](using-cheaderctrl.md)<br/>
[控件](controls-mfc.md)
