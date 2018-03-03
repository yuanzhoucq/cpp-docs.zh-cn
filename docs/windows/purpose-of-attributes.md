---
title: "特性用途 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed20c29d017527d5c2ce0b0c5ab8053fc75dc6ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="purpose-of-attributes"></a>特性用途
属性扩展的 c + + 在不是当前可能的方向而不会破坏语言的经典结构。 属性允许提供程序 (单独的 Dll) 来动态扩展语言功能。 属性的主要目的是简化的 COM 组件，除了提高组件开发人员的工作效率级别创作。 特性可以应用到几乎任何 c + + 构造，如类、 数据成员或成员函数。 下面是这种新技术所提供的优势突出显示：  
  
-   公开熟悉且简单的调用约定。  
  
-   使用插入的代码，这不同于宏，则调试器所识别。  
  
-   允许从基类不需要繁琐的实现详细信息的情况下轻松派生。  
  
-   替换大量的 IDL 代码所需的少数简洁属性的 COM 组件。  
  
 例如，若要实现泛型的 ATL 类的简单事件接收器，可以应用[event_receiver](../windows/event-receiver.md)属性为特定的类，如`CMyReceiver`。 **Event_receiver**属性然后编译 Visual c + + 编译器将适当的代码插入到对象文件。  
  
```  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 你可以然后设置**CMyReceiver**方法`handler1`和`handler2`来处理事件 (使用内部函数[__hook](../cpp/hook.md)) 从事件源，你可以创建使用[event_source](../windows/event-source.md)。  
  
## <a name="see-also"></a>请参阅  
 [概念](../windows/attributed-programming-concepts.md)