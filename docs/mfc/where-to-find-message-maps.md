---
title: 消息映射的位置
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: eec0ae43546e3cc0c08e3178c4808e21fa48686a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360164"
---
# <a name="where-to-find-message-maps"></a>消息映射的位置

使用应用程序向导创建新的骨架应用程序时，应用程序向导会为其创建的每个命令目标类编写一个消息映射。 这包括派生的应用程序、文档、视图和框架窗口类。 其中一些消息映射已包含应用程序向导为某些消息和预定义命令提供的条目，有些只是要添加的处理程序的占位符。

类的消息映射位于 中。类的 CPP 文件。 使用应用程序向导创建的基本消息映射，可以使用[类向导](reference/mfc-class-wizard.md)为每个类将处理的消息和命令添加条目。 添加一些条目后，典型的消息映射可能如下所示：

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

消息映射由宏的集合组成。 两个宏[，BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)和[END_MESSAGE_MAP，](reference/message-map-macros-mfc.md#end_message_map)将消息映射置于括号。 其他宏（如`ON_COMMAND`）将填写消息映射的内容。

> [!NOTE]
> 消息映射宏后面不跟分号。

当您使用"添加类"向导创建新类时，它将为类提供消息映射。 或者，您可以使用源代码编辑器手动创建消息映射。

## <a name="see-also"></a>另请参阅

[框架如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)
