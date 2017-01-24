---
title: "Using the RichEdit 1.0 Control with MFC | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "RichEdit 1.0 control"
  - "rich edit controls, RichEdit 1.0"
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using the RichEdit 1.0 Control with MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

要使用 RichEdit 控件，必须首先调用 [AfxInitRichEdit2](../Topic/AfxInitRichEdit2.md) 以加载 RichEdit 2.0 控件 \(RICHED20.DLL\)，或者调用 [AfxInitRichEdit](../Topic/AfxInitRichEdit.md) 以加载旧的 RichEdit 1.0 控件 \(RICHED32.DLL\)。  
  
 可以对旧的 RichEdit 1.0 控件使用当前的 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) 类，但是 **CRichEditCtrl** 被设计为仅支持 RichEdit 2.0 控件。  由于 RichEdit 1.0 和 RichEdit 2.0 非常相似，因此大多数方法都有效；但请注意 1.0 与 2.0 控件之间是有差异的，因此有些方法可能不能正常工作甚至完全不工作。  
  
## 要求  
 MFC  
  
## 请参阅  
 [Troubleshooting the Dialog Editor](../mfc/troubleshooting-the-dialog-editor.md)   
 [Dialog Editor](../mfc/dialog-editor.md)