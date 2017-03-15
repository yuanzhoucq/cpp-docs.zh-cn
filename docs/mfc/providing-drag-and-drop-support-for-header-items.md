---
title: "为标题项提供拖放支持 | Microsoft Docs"
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
  - "CHeaderCtrl 类, 拖放支持"
  - "HDN_ 通知"
  - "HDS_DRAGDROP 样式"
  - "标题控件中的标题项"
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 为标题项提供拖放支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对标题项若要提供拖放支持，请指定 `HDS_DRAGDROP` 样式。  标题项中对拖放的支持使用户能够重新排序标题控件的标题项。  如果标题项删除，默认行为提供将的标题项的半透明的拖动图像和新位置的一个直观的指示符。  
  
 利用常见的拖放功能，可以通过处理 **HDN\_BEGINDRAG** 和 **HDN\_ENDDRAG** 通知扩展默认拖放行为。  您可以通过 [CHeaderCtrl::CreateDragImage](../Topic/CHeaderCtrl::CreateDragImage.md) 重写成员函数也可自定义的、拖动图像的外观。  
  
> [!NOTE]
>  如果您在列表控件的嵌入式控制标题提供拖放支持，请参见 [更改列表样式控件](../mfc/changing-list-control-styles.md) 主题的扩展样式节。  
  
## 请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)