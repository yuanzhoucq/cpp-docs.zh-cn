---
title: "与 Rich Edit 控件相关的类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类 [C++], 与 Rich Edit 控件相关"
  - "CRichEditCtrl 类, 相关类"
  - "CRichEditCtrlItem 类和 CRichEditCtrl"
  - "CRichEditDoc 类, Rich Edit 控件"
  - "CRichEditView 类, 和 CRichEditCtrl"
  - "Rich Edit 控件, 和 CRichEditDoc"
  - "Rich Edit 控件, 和 CRichEditItem"
  - "Rich Edit 控件, 和 CRichEditView"
  - "Rich Edit 控件, 类相关于"
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 与 Rich Edit 控件相关的类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CRichEditView](../mfc/reference/cricheditview-class.md)、[CRichEditDoc](../mfc/reference/cricheditdoc-class.md) 和 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md) 类提供了 MFC 文档\/视图结构的上下文中的富编辑控件 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 的功能。  `CRichEditView` 保留文本和文本的格式。  `CRichEditDoc` 保留视图中的 OLE 项的客户列表。  `CRichEditCntrItem` 提供容器对 OLE 客户端项的访问。  要修改 `CRichEditView`的内容，请使用 [CRichEditView::GetRichEditCtrl](../Topic/CRichEditView::GetRichEditCtrl.md) 访问基础 Rich Edit 控件。  
  
## 请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)