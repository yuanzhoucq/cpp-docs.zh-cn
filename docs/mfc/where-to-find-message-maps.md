---
title: 消息映射的位置
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: c50c6fc1134f579859530972dc864103c4e0ebcf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907349"
---
# <a name="where-to-find-message-maps"></a>消息映射的位置

使用应用程序向导创建新的主干应用程序时，应用程序向导将为您创建的每个命令目标类写入消息映射。 这包括派生的应用程序、文档、视图和框架窗口类。 其中一些消息映射已经具有应用程序向导为某些消息和预定义的命令提供的条目，而有些则只是要添加的处理程序的占位符。

类的消息映射位于中。类的 CPP 文件。 使用应用程序向导创建的基本消息映射，可使用[类向导](reference/mfc-class-wizard.md)添加每个类将处理的消息和命令的条目。 添加一些条目后，典型的消息映射可能类似于以下内容：

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

消息映射包含宏的集合。 [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)和[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)两个宏，括在消息映射中。 其他宏（如`ON_COMMAND`）填写消息映射的内容。

> [!NOTE]
>  消息映射宏后面不跟分号。

使用 "添加类向导" 创建新类时，它将为类提供消息映射。 或者，您可以使用源代码编辑器手动创建消息映射。

## <a name="see-also"></a>请参阅

[框架如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)
