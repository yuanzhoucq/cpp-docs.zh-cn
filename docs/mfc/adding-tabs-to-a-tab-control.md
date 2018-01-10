---
title: "向选项卡控件添加选项卡 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 46012a265c1ecefa7af63f829be22e6132e036cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-tabs-to-a-tab-control"></a>向选项卡控件添加选项卡
创建选项卡控件之后 ([CTabCtrl](../mfc/reference/ctabctrl-class.md))，添加所需的任意多个选项卡。  
  
### <a name="to-add-a-tab-item"></a>添加选项卡  
  
1.  准备[TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554)结构。  
  
2.  调用[ctabctrl:: Insertitem](../mfc/reference/ctabctrl-class.md#insertitem)，传递结构。  
  
3.  针对其他选项卡项目，重复步骤 1 和 2。  
  
 有关详细信息，请参阅[创建选项卡控件](http://msdn.microsoft.com/library/windows/desktop/bb760550)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控件](../mfc/controls-mfc.md)

