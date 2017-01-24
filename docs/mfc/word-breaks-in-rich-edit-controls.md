---
title: "Rich Edit 控件中的断字 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCtrl 中的断字"
  - "CRichEditCtrl 类, 断字"
  - "Rich Edit 控件, 断字"
  - "断字"
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Rich Edit 控件中的断字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

丰富的编辑控件 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 调用称为“Word 中断过程”功能查找在各单词之间的中断和确定其位置可以分隔线。  控件使用此信息，当执行自动换行操作和处理 CTRL\+LEFT 和 CTRL\+RIGHT 组合键时。  应用程序可以发送消息到富有的编辑控件去替换默认区分词义过程，检索区分词义信息并确定特定字符位于行上。  
  
## 请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)