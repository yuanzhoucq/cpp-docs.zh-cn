---
title: "回调项和回调掩码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24d9992b8a9db679b30624d85ede1a35bfd9826d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="callback-items-and-the-callback-mask"></a>回调项和回调掩码
列表视图控件通常会为它的每一项存储标签文本、项图标的图像列表索引以及表示项状态的一组位标志。 您可以定义单个项作为回调项，当应用程序已经存储某个项的一些信息时，这将很有用。  
  
 通过指定的相应值的项定义为回调项`pszText`和`iImage`的成员**LV_ITEM**结构 (请参阅[clistctrl:: Getitem](../mfc/reference/clistctrl-class.md#getitem))。 如果应用程序维护项或子项的文本，则指定**LPSTR_TEXTCALLBACK**值`pszText`成员。 如果将跟踪应用程序的项的图标，指定**I_IMAGECALLBACK**值`iImage`成员。  
  
 除了定义回调项之外，您还可以修改控件的回调掩码。 此掩码是一组位标志，用于指定应用程序（而不是控件）存储当前数据的项状态。 回调掩码适用于控件的所有项，而回调项指示符则不同，它适用于特定项。 回调掩码默认为零，这意味着控件将跟踪所有项状态。 若要更改此默认行为，请将掩码初始化为以下值的任意组合：  
  
-   `LVIS_CUT`项被标记为剪切和粘贴操作。  
  
-   `LVIS_DROPHILITED`项被标记为拖放目标。  
  
-   `LVIS_FOCUSED`项具有焦点。  
  
-   `LVIS_SELECTED`选择项。  
  
-   **LVIS_OVERLAYMASK**应用程序存储的每个项将当前覆盖图像的图像列表索引。  
  
-   **LVIS_STATEIMAGEMASK**应用程序存储的每个项的当前状态图像的图像列表索引。  
  
 检索和设置此掩码的进一步信息，请参阅[clistctrl:: Getcallbackmask](../mfc/reference/clistctrl-class.md#getcallbackmask)和[clistctrl:: Setcallbackmask](../mfc/reference/clistctrl-class.md#setcallbackmask)。  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)

