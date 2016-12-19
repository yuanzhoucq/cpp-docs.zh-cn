---
title: "事件处理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "特性 [C++], 事件处理"
  - "事件处理, Visual C++"
  - "内部函数, 事件处理"
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 事件处理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

COM 类（实现 COM 对象的 C\+\+ 类，通常使用 ATL 类或 [coclass](../windows/coclass.md) 特性）主要支持事件处理。有关更多信息，请参见 [COM 中的事件处理](../cpp/event-handling-in-com.md)。  
  
 本机 C\+\+ 类（不实现 COM 对象的 C\+\+ 类）也支持事件处理，但将来版本中会弃用并删除此支持。有关详细信息，请参阅[本机 C\+\+ 中的事件处理](../cpp/event-handling-in-native-cpp.md)。  
  
 事件处理支持单线程和多线程用法，并防止数据同时进行多线程访问。  它还允许您从事件源或接收器类派生子类，并支持派生类中的扩展事件源\/接收。  
  
 Visual C\+\+ 包含用于声明事件和事件处理程序的特性和关键字。  事件特性和关键字可用于 CLR 程序和本机 C\+\+ 程序中。  
  
|主题|说明|  
|--------|--------|  
|[event\_source](../windows/event-source.md)|创建事件源。|  
|[event\_receiver](../windows/event-receiver.md)|创建事件接收器（接收器）。|  
|[\_\_event](../cpp/event.md)|声明事件。|  
|[\_\_raise](../cpp/raise.md)|强调一个事件的调用站点。|  
|[\_\_hook](../cpp/hook.md)|将处理程序方法与事件关联。|  
|[\_\_unhook](../cpp/unhook.md)|取消处理程序方法与事件的关联。|  
  
## 请参阅  
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [Event Handling Samples](http://msdn.microsoft.com/zh-cn/cc0287d4-f92b-4da5-85fc-a0f186e16424)