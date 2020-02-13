---
title: 橡皮筋和跟踪器
ms.date: 11/04/2016
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
ms.openlocfilehash: 095f3c15546466c6a495f6aa348990ed69b04a9e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127361"
---
# <a name="rubber-banding-and-trackers"></a>橡皮筋和跟踪器

提供有跟踪器的其他功能是“橡皮筋”选择，该功能允许用户通过围绕要选择的项拖动调整大小矩形来选择多个 OLE 项。 当用户松开鼠标左键后，用户选定区域中的项将选定并且可由用户进行操作。 例如，用户可以将选择拖进另一个容器应用程序。

实现此功能需要应用程序 WM_LBUTTONDOWN 处理程序函数中的一些附加代码。

以下代码示例实现橡皮筋选择和其他功能。

[!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]

如果希望在橡胶条中允许跟踪跟踪器的可逆方向，应调用[CRectTracker：： TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) ，并将第三个参数设置为**TRUE**。 请记住，允许可逆方向有时会导致[CRectTracker：： m_rect](../mfc/reference/crecttracker-class.md#m_rect)反转。 可以通过调用[CRect：： NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect)来更正此情况。

有关详细信息，请参阅[容器客户端项](../mfc/containers-client-items.md)和[OLE 拖放：自定义拖放](../mfc/drag-and-drop-ole.md#customize-drag-and-drop)。

## <a name="see-also"></a>另请参阅

[跟踪器：在 OLE 应用程序内实现跟踪器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)<br/>
[CRectTracker 类](../mfc/reference/crecttracker-class.md)
