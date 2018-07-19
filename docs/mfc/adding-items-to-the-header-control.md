---
title: 将项添加到标头控件 |Microsoft 文档
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
ms.openlocfilehash: 69d64265a94df2770e3a234ab992130b4809f9e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342730"
---
# <a name="adding-items-to-the-header-control"></a>向标题控件添加项
创建标题控件之后 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 在其父窗口中，添加任意多个"标头项"，将需要： 通常每列一个。  
  
### <a name="to-add-a-header-item"></a>添加标题项  
  
1.  准备[HD_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247)结构。  
  
2.  调用[cheaderctrl:: Insertitem](../mfc/reference/cheaderctrl-class.md#insertitem)，传递结构。  
  
3.  对于其他项，重复步骤 1 和 2。  
  
 有关详细信息，请参阅[将项添加到标题控件](http://msdn.microsoft.com/library/windows/desktop/bb775238)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控件](../mfc/controls-mfc.md)

