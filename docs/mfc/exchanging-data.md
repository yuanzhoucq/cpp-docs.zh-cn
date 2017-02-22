---
title: "交换数据 | Microsoft Docs"
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
  - "对话框数据交换 (DDX), 属性表"
  - "与属性表交换数据"
  - "属性表, 数据交换"
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 交换数据
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

与大多数对话框数据交换，在属性表和应用程序之间是的一个属性表的最重要的函数。  本主题介绍如何执行此任务。  
  
 使用属性表的交换数据。实际上是交换数据问题属性表的各个属性页。  因为一个 [CPropertyPage](../mfc/reference/cpropertypage-class.md) 对象仅仅是一个特定的 [CDialog](../mfc/reference/cdialog-class.md) 对象，用属性页交换数据的过程和用对话框交换数据的过程相同。  过程同时利用框架的对话框数据交换 \(DDX\) 结构，在这些控件在对话框和对话框成员变量之间的交换数据对象。  
  
 交换数据之间的重要差异在于将属性表与普通对话框是属性表有多页，因此，必须将所有页的数据交换。属性表。  有关 DDX 的更多信息，请参见 [对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。  
  
 下面的示例阐释在"视图和"属性表的两页的之间交换数据：  
  
 [!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/CPP/exchanging-data_1.cpp)]  
  
## 请参阅  
 [属性表](../mfc/property-sheets-mfc.md)