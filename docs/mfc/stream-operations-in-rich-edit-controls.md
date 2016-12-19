---
title: "Rich Edit 控件中的流操作 | Microsoft Docs"
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
  - "CRichEditCtrl 类, 流操作"
  - "CRichEditCtrl 类, 流存储"
  - "Rich Edit 控件, 流操作"
  - "存储, CRichEditCtrl 中的流"
  - "CRichEditCtrl 中的流操作"
  - "流存储和 CRichEditCtrl"
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Rich Edit 控件中的流操作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用将数据传输到流或流出丰富的编辑控件 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\)。  流由 [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) 结构定义，指定缓冲区和应用程序定义的回调函数。  
  
 若要数据读入丰富的编辑控件 \(即中流数据\)，请使用 [StreamIn](../Topic/CRichEditCtrl::StreamIn.md) 成员函数。  控件重复调用应用程序定义的回调函数，每次的数据传输部分放到缓冲区。  
  
 若要保存丰富的编辑控件的内容 \(即中流数据\)，可以使用 [StreamOut](../Topic/CRichEditCtrl::StreamOut.md) 成员函数。  到缓冲区中将重复控件编写然后调用应用程序定义的回调函数。  对于每个调用，回调函数保存缓冲区的内容。  
  
## 请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)