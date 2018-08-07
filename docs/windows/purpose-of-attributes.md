---
title: 特性用途 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2ca7757c1b9a8ebf034f68b9a380c09d4a5b08f1
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607019"
---
# <a name="purpose-of-attributes"></a>特性用途
属性扩展的 c + + 中当前不可能的方向而不会破坏经典的语言结构。 属性允许提供程序 (单独的 Dll) 来动态扩展语言功能。 属性的主要目标是简化 COM 组件以及增加组件开发人员的工作效率级别的创作。 属性可应用于几乎任何 c + + 构造，如类、 数据成员或成员函数。 下面是提供这项新技术的优势的突出显示：  
  
-   公开熟悉且简单的调用约定。  
  
-   使用插入的代码，这不同于宏，调试器所识别。  
  
-   允许简单而无需繁重的实现详细信息的基类派生。  
  
-   取代了大量的 IDL 代码所需的少量简洁属性具有的 COM 组件。  
  
 例如，若要实现泛型 ATL 类的简单事件接收器，可以应用[event_receiver](../windows/event-receiver.md)特性为特定的类如`CMyReceiver`。 `event_receiver`属性然后编译的 Visual c + + 编译器，它将正确的代码插入到对象文件。  
  
```  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 然后可以设置`CMyReceiver`方法`handler1`并`handler2`来处理事件 (使用内部函数[__hook](../cpp/hook.md)) 的事件源，可以创建使用[event_source](../windows/event-source.md).  
  
## <a name="see-also"></a>请参阅  
 [概念](../windows/attributed-programming-concepts.md)