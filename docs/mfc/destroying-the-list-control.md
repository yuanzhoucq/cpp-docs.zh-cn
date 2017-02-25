---
title: "销毁列表控件 | Microsoft Docs"
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
  - "CListCtrl 类, 销毁控件"
  - "列表控件, 销毁"
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 销毁列表控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果嵌入 [CListCtrl](../mfc/reference/clistctrl-class.md) 对象作为视图或在对话框类的数据成员，销毁它，在销毁时其所有者。  如果将使用 [CListView](../mfc/reference/clistview-class.md)，销毁框架控件，则销毁时视图。  
  
 如果您已在应用程序中存储的某些列表数据而不是列表控件，需要将其释放。  有关更多信息，请参见" [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [回调项和回调掩码](http://msdn.microsoft.com/library/windows/desktop/bb774736)。  
  
 此外，您负责释放已经创建并与列表控件关联的对象列表中的所有图像。  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)