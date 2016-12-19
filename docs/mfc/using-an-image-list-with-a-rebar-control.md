---
title: "对 Rebar 控件使用图像列表 | Microsoft Docs"
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
  - "图像列表 [C++], rebar 控件"
  - "rebar 控件, 图像列表"
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对 Rebar 控件使用图像列表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个rebar 带可以包含在其他事中的从关联的图像列表里的图像。  以下过程详细描述在rebar带显示图像的必要步骤。  
  
### 在rebar带中显示图像  
  
1.  附加图像列表到 rebar 控件，通过调用 [SetImageList](../Topic/CReBarCtrl::SetImageList.md)，将指针传递给现有图像列表。  
  
2.  修改 **REBARBANDINFO** 结构以分配图像到 rebar 带：  
  
    -   按位设置 **fMask** 成员设置为 **RBBIM\_IMAGE**，使用按位 OR 运算符以包含需要的标志。  
  
    -   将 `iImage` 成员设置为要显示图像的图像列表索引。  
  
3.  初始化其余的数据成员，如大小，文本和包含子窗口的句柄，使用必要的信息。  
  
4.  插入新的带区 \(使用图像\)，调用[CReBarCtrl::InsertBand](../Topic/CReBarCtrl::InsertBand.md)，将传递**REBARBANDINFO** 结构。  
  
 下面的示例假定两个图像的现有图像列表对象附加到 rebar 控件对象 \(`m_wndReBar`\)。  新的rebar带 \(定义带 `rbi`\)，其中包含第一个图像，添加一个对`InsertBand`的调用：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/CPP/using-an-image-list-with-a-rebar-control_1.cpp)]  
  
## 请参阅  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控件](../mfc/controls-mfc.md)