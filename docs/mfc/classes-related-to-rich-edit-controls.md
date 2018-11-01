---
title: 与 Rich Edit 控件相关的类
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], and CRichEditItem
- CRichEditCtrl class [MFC], related classes
- CRichEditDoc class [MFC], Rich Edit controls
- rich edit controls [MFC], classes related to
- classes [MFC], related to rich edit controls
- rich edit controls [MFC], and CRichEditView
- CRichEditCtrlItem class and CRichEditCtrl
- rich edit controls [MFC], and CRichEditDoc
- CRichEditView class [MFC], and CRichEditCtrl
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
ms.openlocfilehash: 92134d0bd4d02bff7aeadd5e9ca7438c61de3bec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586155"
---
# <a name="classes-related-to-rich-edit-controls"></a>与 Rich Edit 控件相关的类

[CRichEditView](../mfc/reference/cricheditview-class.md)， [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)，并[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)类提供了 rich edit 控件的功能 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))在 MFC 文档/视图体系结构的上下文。 `CRichEditView` 保留文本及其格式特征。 `CRichEditDoc` 保留视图中的 OLE 客户端项的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。 若要修改的内容`CRichEditView`，使用[cricheditview:: Getricheditctrl](../mfc/reference/cricheditview-class.md#getricheditctrl)来访问基础 rich edit 控件。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

