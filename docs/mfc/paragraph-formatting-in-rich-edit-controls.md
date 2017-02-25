---
title: "Rich Edit 控件中的段落格式设置 | Microsoft Docs"
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
  - "CRichEditCtrl 类, 段落格式设置"
  - "格式设置 [C++], 段"
  - "CRichEditCtrl 中的段落格式设置"
  - "Rich Edit 控件, 段落格式设置"
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Rich Edit 控件中的段落格式设置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用丰富的编辑控件 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 的成员函数形成段落和检索格式设置信息。  段落格式特性包括对齐、选项卡、缩进和数字。  
  
 使用 [SetParaFormat](../Topic/CRichEditCtrl::SetParaFormat.md) 成员函数，可应用段落格式。  若要确定当前选择的文本的段落格式，请使用 [GetParaFormat](../Topic/CRichEditCtrl::GetParaFormat.md) 成员函数。  [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) 结构来提供这些成员函数指定的特性。  某一 **PARAFORMAT** 的重要成员是 **dwMask**。  在 `SetParaFormat`中，**dwMask** 指定由函数调用设置的段落属性。  在选择中，报告第一个段落的`GetParaFormat` 特性；**dwMask** 指定选择一致的属性。  
  
## 请参阅  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控件](../mfc/controls-mfc.md)