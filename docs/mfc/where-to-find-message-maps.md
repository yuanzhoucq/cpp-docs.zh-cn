---
title: 消息映射的位置
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: d9b9a50062334822f34047b8e22e67541ccaa952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217849"
---
# <a name="where-to-find-message-maps"></a>消息映射的位置

当使用应用程序向导创建新的主干应用程序时，应用程序向导为您编写消息映射为它创建每个命令目标类。 这包括你派生应用程序、 文档、 视图和框架窗口类。 这些消息映射的一些已由应用程序向导为特定的消息和预定义的命令，提供的条目，有些则将添加的处理程序只是占位符。

类的消息映射位于中。类的 CPP 文件。 使用应用程序向导创建基本的消息映射，使用属性窗口的消息和命令的每个类将处理为添加项。 添加一些项后，典型的消息映射可能如下所示：

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

消息映射的宏的集合组成。 两个宏[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)并[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)，方括号消息映射。 其他宏，如`ON_COMMAND`，填写消息映射的内容。

> [!NOTE]
>  消息映射宏的后面没有分号分隔。

当你使用添加类向导创建一个新类时，它为类提供消息映射。 或者，可以创建手动使用源代码编辑器的消息映射。

## <a name="see-also"></a>请参阅

[框架如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)
