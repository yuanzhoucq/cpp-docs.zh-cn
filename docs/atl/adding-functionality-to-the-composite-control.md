---
title: 向复合控件添加功能
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 5de18f863831973af384d2456adb5b2214f0dd68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317427"
---
# <a name="adding-functionality-to-the-composite-control"></a>向复合控件添加功能

将任何必要的控件插入到复合控件中后，下一步将添加新功能。 此新功能通常分为两类：

- 支持其他接口，并自定义复合控件的行为与其他特定功能。

- 从包含的 ActiveX 控件（或控件）处理事件。

就本文的目的和范围而言，本节的其余部分仅侧重于处理来自 ActiveX 控件的事件。

> [!NOTE]
> 如果需要处理来自 Windows 控件的消息，请参阅[实现窗口](../atl/implementing-a-window.md)，了解有关 ATL 中邮件处理的详细信息。

在对话框资源中插入 ActiveX 控件后，右键单击该控件并单击"**添加事件处理程序**"。 选择要处理的事件，然后单击"**添加和编辑**"。 事件处理程序代码将添加到控件的 .h 文件中。

复合控件上的 ActiveX 控件的连接点通过呼叫[CCom复合控制系统自动连接和断开连接：：建议SinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)。

## <a name="see-also"></a>另请参阅

[复合控件基础知识](../atl/atl-composite-control-fundamentals.md)
