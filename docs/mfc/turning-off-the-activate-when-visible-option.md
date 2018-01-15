---
title: "关闭激活时可见选项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 25521d75921b377730a7f9afac71f2a60c055216
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="turning-off-the-activate-when-visible-option"></a>关闭“可见时激活”选项
控件有两种基本状态： 活动和非活动。 传统上，控件是否有一个窗口来区分这些状态。 活动控件有窗口;不支持非活动控件。 随着无窗口激活的推出，这一区别不再通用的但仍然适用于很多控件。  
  
 与通常由 ActiveX 控件执行的初始化的其余工作相比，创建窗口是一个资源消耗很大的操作。 理想情况下，控件会推迟创建其窗口，直到非要执行此操作。  
  
 许多控件在其在容器中可见的整个时间不需要是活动的。 通常，控件可保持不活动状态，直到用户执行需要此控件变为活动状态的操作（例如，使用鼠标单击或按 Tab 键）。 若要使控件容器需要激活它之前保持非活动状态，请删除**OLEMISC_ACTIVATEWHENVISIBLE**从控件的杂项标志的标志：  
  
 [!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]  
  
 **OLEMISC_ACTIVATEWHENVISIBLE**如果关闭，则将自动省略标志**可见时激活**选项[控制设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md)MFC ActiveX 页当您在创建控件时控件向导。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)

