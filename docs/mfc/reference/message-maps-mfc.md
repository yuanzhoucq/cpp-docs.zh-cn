---
title: 消息映射 (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 8080becf1a1a153322bfd03cbd7006eaf2ce4e13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356579"
---
# <a name="message-maps-mfc"></a>消息映射 (MFC)

引用的这一部分列出了所有[消息映射宏](../../mfc/reference/message-map-macros-mfc.md)和所有[CWnd](../../mfc/reference/cwnd-class.md)消息映射条目以及相应的成员函数原型：

|类别|说明|
|--------------|-----------------|
|打开\_COMMAND 消息处理程序|处理`WM_COMMAND`用户菜单选择或菜单访问键生成的消息。|
|[子窗口通知消息处理程序](../../mfc/reference/child-window-notification-message-handlers.md)|处理来自子窗口的通知消息。|
|[WM_消息处理程序](../../mfc/reference/handlers-for-wm-messages.md)|处理`WM_`消息，如`WM_PAINT`。|
|[用户定义的消息处理程序](../../mfc/reference/user-defined-handlers.md)|处理用户定义的消息。|

（有关此参考中使用的术语和约定的说明，请参阅[如何使用消息映射交叉引用](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)。

由于 Windows 是面向消息的操作系统，因此 Windows 环境的大部分编程涉及消息处理。 每次发生按键或鼠标单击等事件时，都会向应用程序发送消息，应用程序必须处理该事件。

Microsoft 基础类库提供了针对基于消息的编程优化的编程模型。 在此模型中，"消息映射"用于指定哪些函数将处理特定类的各种消息。 消息映射包含一个或多个宏，用于指定哪些消息将由哪些函数处理。 例如，包含`ON_COMMAND`宏的消息映射可能如下所示：

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

该`ON_COMMAND`宏用于处理由菜单、按钮和快捷键生成的命令消息。 [宏](../../mfc/reference/message-map-macros-mfc.md)可用于映射以下内容：

## <a name="windows-messages"></a>窗口消息

- 控制通知

- 用户定义的消息

## <a name="command-messages"></a>命令消息

- 已注册用户定义的消息

- 用户界面更新消息

## <a name="ranges-of-messages"></a>消息范围

- 命令

- 更新处理程序消息

- 控制通知

尽管消息映射宏很重要，但通常不必直接使用它们。 这是因为[类向导](mfc-class-wizard.md)在使用源文件中自动创建消息映射条目，将消息处理函数与消息相关联。 任何时候要编辑或添加消息映射条目时，都可以使用类向导。

> [!NOTE]
> 类向导不支持消息映射范围。 您必须自己编写这些消息映射条目。

但是，消息映射是 Microsoft 基础类库的重要组成部分。 您应该了解它们做什么，并为它们提供文档。

## <a name="see-also"></a>另请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
