---
title: 在哪里可以找到消息映射 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19dfaec7d97bed560665fce25c2ddf2cc816a483
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="where-to-find-message-maps"></a>消息映射的位置
当使用应用程序向导创建新的主干应用程序时，应用程序向导为您编写它会创建每个命令目标类的消息映射。 这包括你派生应用程序、 文档、 视图和框架窗口类。 这些消息映射的某些已提供某些消息和预定义的命令，则应用程序向导的条目，而有些则只需将添加的处理程序的占位符。  
  
 类的消息映射位于中。类的 CPP 文件。 使用应用程序向导创建基本消息映射，使用属性窗口以添加条目的消息和每个类将处理的命令。 你添加一些项后，典型的消息映射可能如下所示：  
  
 [!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]  
  
 消息映射包含宏的集合。 两个宏[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)和[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)，括号的消息映射。 其他宏，如`ON_COMMAND`，填写消息映射的内容。  
  
> [!NOTE]
>  消息映射宏不后跟分号。  
  
 当你使用添加类向导创建一个新类时，它为类提供消息映射。 或者，你可以创建使用源代码编辑器手动消息映射。  
  
## <a name="see-also"></a>请参阅  
 [框架如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)

