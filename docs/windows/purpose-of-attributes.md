---
title: "Purpose of Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], about attributes"
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Purpose of Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

属性超出方向 C\+\+ 当前不可能，但不会中断该语言的经典结构。  属性允许提供程序 \(单独的 DLL\) 动态扩展语言功能。  属性的主要目的是为了简化生成 COM 组件，除了增加组件开发人员的工作效率级别之外。  特性可应用到几乎所有 C\+\+ 构造，如类、数据成员或成员函数。  下面是该新技术提供的优点突出显示:  
  
-   显示一个熟悉和简单的调用约定。  
  
-   插入的使用代码，不同，宏，由调试器识别。  
  
-   允许从基类的简单的派生，而不需要谨记沉重的实现详细信息。  
  
-   但也使用属性替换 COM 组件所需的大量 IDL 代码。  
  
 例如，实现泛型 ATL 类的简单事件接收器，可以将 [event\_receiver](../windows/event-receiver.md) 特性应用于特定类 \(如 `CMyReceiver`。  **event\_receiver** 属性由 Visual C\+\+ 编译器然后生成，插入适当的代码添加到对象文件中。  
  
```  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 然后可以设置 **CMyReceiver** 方法 `handler1` 和 `handler2` 处理事件 \(使用内部函数 [\_\_hook](../cpp/hook.md)\) 从事件源，使用 [event\_source](../windows/event-source.md)，可以创建一个。  
  
## 请参阅  
 [Concepts](../windows/attributed-programming-concepts.md)