---
title: 将功能添加到复合控件 |Microsoft Docs
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
ms.openlocfilehash: 59ee8047e17efdebbae6ee58ec243057a477caff
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751128"
---
# <a name="adding-functionality-to-the-composite-control"></a>将功能添加到复合控件

一旦已插入到复合控件的任何必要的控件下, 一步涉及添加新功能。 这一新功能通常分为两类：

- 支持附加的接口和自定义复合控件与其他的特定功能的行为。

- 处理包含 ActiveX 控件 （或控件） 中的事件。

对于用途和本文的讨论范围，此部分的其余部分只集中讨论如何处理 ActiveX 控件中的事件。

> [!NOTE]
>  如果您需要处理来自 Windows 控件的消息，请参阅[实现窗口](../atl/implementing-a-window.md)的 ATL 中处理的消息的详细信息

之后将 ActiveX 控件插入对话框资源中，右键单击该控件，然后单击**添加事件处理程序**。 选择你想要处理单击的事件**添加和编辑**。 事件处理程序代码将添加到控件的.h 文件。

复合控件上的 ActiveX 控件的连接点自动连接，并通过调用断开[CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)。

## <a name="see-also"></a>请参阅

[复合控件基础知识](../atl/atl-composite-control-fundamentals.md)

