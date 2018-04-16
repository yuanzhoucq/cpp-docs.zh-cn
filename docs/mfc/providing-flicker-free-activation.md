---
title: 提供无闪烁激活 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f14998ce663e5a8e53901acf9192719fa41e724
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="providing-flicker-free-activation"></a>提供无闪烁激活
如果控件处于非活动和活动状态相同绘制本身 （和不使用无窗口激活），则可以消除绘制操作和伴随通常发生在进行间处于非活动状态的转换时的可视闪烁和活动状态。 若要执行此操作，包括**noFlickerActivate**标志返回集中的标志[COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags)。 例如:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]  
  
 如果你选择自动生成代码以包括此标志**闪烁激活**选项[控制设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md)页上使用 MFC ActiveX 控件向导创建控件时。  
  
 如果使用无窗口激活，则此优化不起作用。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)

