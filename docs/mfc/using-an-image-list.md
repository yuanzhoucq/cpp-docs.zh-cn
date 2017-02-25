---
title: "使用图像列表 | Microsoft Docs"
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
  - "CImageList 类, using"
  - "图像列表 [C++]"
  - "列表 [C++], 图像"
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用图像列表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

图像列表的典型用法遵循以下模式：  
  
-   [CImageList](../mfc/reference/cimagelist-class.md) 构造对象并调用一个 [创建](../Topic/CImageList::Create.md) 其函数重载生成图像列表并将其附加到 `CImageList` 对象。  
  
-   如果未添加图像，如果创建图像列表，请将图像添加到图像列表通过调用 [添加](../Topic/CImageList::Add.md)[读取](../Topic/CImageList::Read.md) 或成员函数。  
  
-   使用图像列表的函数 [绘制](../Topic/CImageList::Draw.md) 成员，将图像列表与控件通过调用该控件的相应成员函数或是从图像列表中绘制图像。  
  
-   使用将列表中，图像的内置支持可能使用户拖动图像。  
  
> [!NOTE]
>  如果图像列表使用 **new** 运算符创建，则必须销毁 `CImageList` 对象，当您用它。  
  
## 请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)