---
title: 事件处理
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
ms.openlocfilehash: cf16ea0e6e14981f1105456a5f17d68c05a9c3fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189203"
---
# <a name="event-handling"></a>事件处理

通常，COM 类（C++实现 com 对象的类，通常使用 ATL 类或[coclass](../windows/coclass.md)特性）支持事件处理。 有关详细信息，请参阅[COM 中的事件处理](../cpp/event-handling-in-com.md)。

本机 C++ 类（不实现 COM 对象的 C++ 类）也支持事件处理，但将来版本中会弃用并删除此支持。  有关详细信息，请参阅[本机C++中的事件处理](../cpp/event-handling-in-native-cpp.md)。

事件处理支持单线程和多线程用法，并防止数据同时进行多线程访问。 它还允许您从事件源或接收器类派生子类，并支持派生类中的扩展事件源/接收。

Microsoft C++编译器包含用于声明事件和事件处理程序的属性和关键字。 事件特性和关键字可用于 CLR 程序和本机 C++ 程序中。

|主题|说明|
|-----------|-----------------|
|[event_source](../windows/attributes/event-source.md)|创建事件源。|
|[event_receiver](../windows/attributes/event-receiver.md)|创建事件接收器（接收器）。|
|[__event](../cpp/event.md)|声明事件。|
|[__raise](../cpp/raise.md)|强调一个事件的调用站点。|
|[__hook](../cpp/hook.md)|将处理程序方法与事件关联。|
|[__unhook](../cpp/unhook.md)|取消处理程序方法与事件的关联。|

## <a name="see-also"></a>另请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[关键字](../cpp/keywords-cpp.md)
