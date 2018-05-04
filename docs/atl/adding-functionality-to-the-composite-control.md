---
title: 将功能添加到复合控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67602e16fc5a30c82e82772b6b9f6c553ba79d9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
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

