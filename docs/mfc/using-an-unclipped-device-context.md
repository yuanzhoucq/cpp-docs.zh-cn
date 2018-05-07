---
title: 使用未剪辑的设备上下文 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c76dc44993615e17ea3d99f9ac018a748e24d0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="using-an-unclipped-device-context"></a>使用未剪辑的设备上下文
如果您完全确定您的控件不会在其客户端矩形的外部进行绘制，则可以通过禁用对由 `IntersectClipRect` 创建的 `COleControl` 的调用来实现较小但可检测到的增速。 若要执行此操作，请删除**clipPaintDC**从组返回的标志的标志[COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags)。 例如：  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]  
  
 如果你选择自动生成的代码用于删除此标志**未剪辑的设备上下文**选项[控制设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md)页上，使用 MFC ActiveX 控件向导创建控件时。  
  
 如果使用无窗口激活，则此优化不起作用。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)

