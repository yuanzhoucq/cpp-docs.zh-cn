---
title: "弱引用和中断循环 (C + + /cli CX) |Microsoft 文档"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a98dc4dd43b40f378a91713770c4c5500c790d0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>弱引用和中断循环 (C++/CX)
在基于引用计数的任何类型的系统中，对类型的引用可以形成 *循环*，即第一个对象引用第二个对象，第二个对象引用第三个对象，依此类推，直到某个最终对象引用回第一个对象。 在一个循环中，当一个对象的引用计数变为零时，将无法正确删除该对象。 若要帮助你解决此问题，C + + /cli CX 提供[platform:: weakreference 类](../cppcx/platform-weakreference-class.md)类。 `WeakReference` 对象支持 [Resolve](../cppcx/platform-weakreference-class.md#resolve) 方法，如果对象不再存在，则返回 Null，或如果对象是活动的但不是类型 [，则将引发](../cppcx/platform-invalidcastexception-class.md) Platform::InvalidCastException `T`。  
  
 必须使用 `WeakReference` 的一种情况是，在用于定义事件处理程序的 lambda 表达式中捕获 `this` 指针时。 建议你在定义事件处理程序时使用命名的方法，但如果你要对事件处理程序使用 lambda，或者必须在其他某种情况下中断引用计数循环，请使用 `WeakReference`。 以下是一个示例：  
  
```  
  
using namespace Platform::Details;  
using namespace Windows::UI::Xaml;  
using namespace Windows::UI::Xaml::Input;  
using namespace Windows::UI::Xaml::Controls;  
  
Class1::Class1()  
{  
    // Class1 has a reference to m_Page  
    m_Page = ref new Page();  
  
    // m_Page will have a reference to this Class1  
    // so create a weak reference to this  
    WeakReference wr(this);  
    m_Page->DoubleTapped += ref new DoubleTappedEventHandler(   
        [wr](Object^ sender, DoubleTappedRoutedEventArgs^ args)  
    {  
       // Use the weak reference to get the object  
       Class1^ c = wr.Resolve<Class1>();  
       if (c != nullptr)  
       {  
           c->m_eventFired = true;  
       }  
       else  
       {  
           // Inform the event that this handler should be removed  
           // from the subscriber list  
           throw ref new DisconnectedException();  
       }  
    });   
}  
  
}  
```  
  
 当事件处理程序引发 `DisconnectedException` 时，将导致该事件从订阅方列表中将处理程序移除。  
  
## <a name="see-also"></a>请参阅  


