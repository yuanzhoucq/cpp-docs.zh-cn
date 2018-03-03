---
title: "将功能添加到复合控件 |Microsoft 文档"
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
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6dcf3ffa0c3168c2f96a3ad9bed13ab1213f63da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-functionality-to-the-composite-control"></a>将功能添加到复合控件
一旦你已将任何必要的控件插入复合控件下, 一步涉及添加新功能。 此新功能通常分为两类：  
  
-   支持附加的接口和自定义与附加的特定功能你复合控件的行为。  
  
-   处理包含 ActiveX 控件 （或控件） 中的事件。  
  
 目的和本文的讨论范围，此部分的剩余重点在于处理 ActiveX 控件中的事件。  
  
> [!NOTE]
>  如果你需要以处理来自 Windows 控件的消息，请参阅[实现窗口](../atl/implementing-a-window.md)有关详细信息消息处理在 atl。  
  
 后将 ActiveX 控件插入对话框资源中，右击该控件，并单击**添加事件处理程序**。 选择你想要处理并单击的事件**添加和编辑**。 事件处理程序代码将添加到控件的.h 文件。  
  
 复合控件上的 ActiveX 控件的连接点自动连接，并通过调用断开连接[CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)。  
  
## <a name="see-also"></a>请参阅  
 [复合控件基础知识](../atl/atl-composite-control-fundamentals.md)

