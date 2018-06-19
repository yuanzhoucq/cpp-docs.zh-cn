---
title: 对标题控件中的项排序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DS_DRAGDROP
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dfa84326286b03f3ed0154138ed7f847440df284
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347147"
---
# <a name="ordering-items-in-the-header-control"></a>对标题控件中的项排序
之后[项添加到标题控件](../mfc/adding-items-to-the-header-control.md)，您可以操作它们或获取有关它们的顺序使用以下函数的信息：  
  
-   [Cheaderctrl:: Getorderarray](../mfc/reference/cheaderctrl-class.md#getorderarray)和[cheaderctrl:: Setorderarray](../mfc/reference/cheaderctrl-class.md#setorderarray)  
  
     检索和设置标题项的从左到右的顺序。  
  
-   [Cheaderctrl:: Ordertoindex](../mfc/reference/cheaderctrl-class.md#ordertoindex)。  
  
     检索特定标题项的索引值。  
  
 除了前面成员函数外，`HDS_DRAGDROP` 样式也可以让用户在标题控件中拖放标题项。 有关详细信息，请参阅[为标题项提供拖放支持](../mfc/providing-drag-and-drop-support-for-header-items.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)

