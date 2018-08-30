---
title: 将项添加到标头控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6450d99b8df436c64337e52fc14244ecbb0edfc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206142"
---
# <a name="adding-items-to-the-header-control"></a>向标题控件添加项
之后创建标题控件 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 在其父窗口中，添加任意多个"标头项"所需： 通常每列一个。  
  
### <a name="to-add-a-header-item"></a>添加标题项  
  
1.  准备[HD_ITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema)结构。  
  
2.  调用[cheaderctrl:: Insertitem](../mfc/reference/cheaderctrl-class.md#insertitem)，并传入此结构。  
  
3.  对于其他项，重复步骤 1 和 2。  
  
 有关详细信息，请参阅[将项添加到标头控件](/windows/desktop/Controls/header-controls)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控件](../mfc/controls-mfc.md)

