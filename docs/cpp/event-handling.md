---
title: "事件处理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- attributes [C++], event handling
- intrinsic functions [C++], event handling
- event handling [C++], Visual C++
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4167a76d3e301f76ebba09f78abcd7e64fc7f108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="event-handling"></a>事件处理
COM 类主要支持事件处理 (实现 COM 对象，通常使用 ATL 类的 c + + 类或[组件类](../windows/coclass.md)属性)。  有关详细信息，请参阅[COM 中的事件处理](../cpp/event-handling-in-com.md)。  
  
 本机 C++ 类（不实现 COM 对象的 C++ 类）也支持事件处理，但将来版本中会弃用并删除此支持。  有关详细信息，请参阅[本机 c + + 中的事件处理](../cpp/event-handling-in-native-cpp.md)。  
  
 事件处理支持单线程和多线程用法，并防止数据同时进行多线程访问。 它还允许您从事件源或接收器类派生子类，并支持派生类中的扩展事件源/接收。  
  
 Visual C++ 包含用于声明事件和事件处理程序的特性和关键字。 事件特性和关键字可用于 CLR 程序和本机 C++ 程序中。  
  
|主题|描述|  
|-----------|-----------------|  
|[event_source](../windows/event-source.md)|创建事件源。|  
|[event_receiver](../windows/event-receiver.md)|创建事件接收器（接收器）。|  
|[__event](../cpp/event.md)|声明事件。|  
|[__raise](../cpp/raise.md)|强调一个事件的调用站点。|  
|[__hook](../cpp/hook.md)|将处理程序方法与事件关联。|  
|[__unhook](../cpp/unhook.md)|取消处理程序方法与事件的关联。|  
  
## <a name="see-also"></a>请参阅  
 [C + + 语言参考](../cpp/cpp-language-reference.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [事件处理示例](http://msdn.microsoft.com/en-us/cc0287d4-f92b-4da5-85fc-a0f186e16424)