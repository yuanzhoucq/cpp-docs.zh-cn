---
title: "派生消息映射 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e5901602368e60a3873a1dba2fc681c6ac146f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="derived-message-maps"></a>派生消息映射
消息处理期间，检查类自己的消息映射是否是消息映射描述的结尾。 如果会发生什么情况类`CMyView`(派生自`CView`) 的消息没有匹配项  
  
 记住，`CView`（`CMyView` 的基类）是依次从 `CWnd` 派生的。 因此`CMyView`*是*`CView`和*是* `CWnd`。 这些类都有其自己的消息映射。 下图“视图层次结构”显示了类的层次关系，但记住，`CMyView` 对象是具有所有树类的特征的单个对象。  
  
 ![视图层次结构](../mfc/media/vc38621.gif "vc38621")  
视图层次结构  
  
 因此，如果消息无法在类 `CMyView` 的消息映射中匹配，则框架还将在其即时基类中搜索消息映射。 位于消息映射开头的 `BEGIN_MESSAGE_MAP` 宏将指定两个类名称作为其参数：  
  
 [!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/cpp/derived-message-maps_1.cpp)]  
  
 第一个自变量命名消息映射所属的类。 第二个参数提供与即时基类 `CView` 的关系，以便框架也可搜索其消息映射。  
  
 基类中提供的消息处理程序将由派生类集成。 这非常类似于标准虚拟成员函数，无需使所有处理程序成员函数成为虚拟。  
  
 如果在任何基类消息映射中都未找到处理程序，则将对消息执行默认处理。 如果消息是命令，则框架会将其路由至下一命令目标。 如果消息是标准 Windows 消息，则消息将传递给适当的默认窗口程序。  
  
 为了加快消息映射匹配，框架将根据再次收到相同的消息的可能性缓存最近的匹配项。 这样做的一个结果就是框架将非常高效地处理未处理的消息。 消息映射还比使用虚函数的实现更省空间。  
  
## <a name="see-also"></a>请参阅  
 [框架如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)

