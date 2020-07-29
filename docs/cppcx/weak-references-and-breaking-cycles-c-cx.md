---
title: 弱引用和中断循环 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
ms.openlocfilehash: 04ba70c148121de520b470bd727b26e756858011
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214927"
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>弱引用和中断循环 (C++/CX)

在基于引用计数的任何类型的系统中，对类型的引用可以形成 *循环*，即第一个对象引用第二个对象，第二个对象引用第三个对象，依此类推，直到某个最终对象引用回第一个对象。 在一个循环中，当一个对象的引用计数变为零时，将无法正确删除该对象。 为了帮助解决此问题，c + +/CX 提供了[Platform：： WeakReference 类](../cppcx/platform-weakreference-class.md)。 `WeakReference` 对象支持 [Resolve](../cppcx/platform-weakreference-class.md#resolve) 方法，如果对象不再存在，则返回 Null，或如果对象是活动的但不是类型 [，则将引发](../cppcx/platform-invalidcastexception-class.md) Platform::InvalidCastException `T`。

必须使用的一种情况 `WeakReference` 是， **`this`** 在用于定义事件处理程序的 lambda 表达式中捕获指针时。 建议你在定义事件处理程序时使用命名的方法，但如果你要对事件处理程序使用 lambda，或者必须在其他某种情况下中断引用计数循环，请使用 `WeakReference`。 下面是一个示例：

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

当事件处理程序引发 `DisconnectedException`时，将导致该事件从订阅方列表中将处理程序移除。
