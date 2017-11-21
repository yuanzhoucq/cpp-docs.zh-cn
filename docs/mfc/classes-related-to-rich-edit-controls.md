---
title: "与 Rich Edit 控件相关的类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 55b44085024902c3edb30f222fa48441fc9e72ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="classes-related-to-rich-edit-controls"></a>与 Rich Edit 控件相关的类
[CRichEditView](../mfc/reference/cricheditview-class.md)， [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)，和[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)类提供 rich edit 控件的功能 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))在 MFC 文档/视图体系结构的上下文。 `CRichEditView` 保留文本及其格式特征。 `CRichEditDoc` 保留视图中的 OLE 客户端项的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。 若要修改的内容`CRichEditView`，使用[cricheditview:: Getricheditctrl](../mfc/reference/cricheditview-class.md#getricheditctrl)来访问基础 rich edit 控件。  
  
## <a name="see-also"></a>另请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)

