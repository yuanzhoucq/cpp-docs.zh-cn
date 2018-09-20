---
title: 处理反射消息 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99fc9c30ea85ba3f94fa811464f023da0eeea37e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438673"
---
# <a name="handling-reflected-messages"></a>处理反射消息

消息反射可以让你处理消息的控件，如**WM_CTLCOLOR**， **WM_COMMAND**，并**WM_NOTIFY**，控件自身。 这使得控件更独立和可移植。 此机制适用于 Windows 公共控件以及 ActiveX 控件（之前称为 OLE 控件）。

消息反射可以让您轻松地重用 `CWnd` 派生类。 消息反射通过[CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)，使用特殊**ON_XXX_REFLECT**消息映射条目： 例如， **ON_CTLCOLOR_REFLECT**和**ON_CONTROL_REFLECT**。 [技术说明 62](../mfc/tn062-message-reflection-for-windows-controls.md)介绍了更多详细信息中的消息反射。

## <a name="what-do-you-want-to-do"></a>你想要做什么

- [了解有关消息反射的详细信息](../mfc/tn062-message-reflection-for-windows-controls.md)

- [实现公共控件的消息反射](../mfc/tn062-message-reflection-for-windows-controls.md)

- [实现 ActiveX 控件的消息反射](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>请参阅

[声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)
