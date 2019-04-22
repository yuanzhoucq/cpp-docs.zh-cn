---
title: 使用 IDispEventSimpleImpl (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
ms.openlocfilehash: 40edca3a99fb6e9d57d617e79d0bd37ebbfcd4ad
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768559"
---
# <a name="using-idispeventsimpleimpl"></a>使用 IDispEventSimpleImpl

当使用`IDispEventSimpleImpl`来处理事件，你将需要：

- 从类派生[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)。

- 将事件接收器映射添加到您的类。

- 定义[_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md)描述事件的结构。

- 将条目添加到使用事件接收器映射[SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info)宏。

- 实现你感兴趣处理的方法。

- 通知和取消通知事件源。

## <a name="example"></a>示例

下面的示例演示如何处理`DocumentChange`由 Word 的事件触发**应用程序**对象。 此事件指一种方法上`ApplicationEvents`调度接口。

该示例摘自[ATLEventHandling 示例](../overview/visual-cpp-samples.md)。

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

该示例使用`#import`从 Word 的类型库生成必需的标头文件。 如果你想要使用此示例与其他版本的 Word，则必须指定正确 mso dll 文件。 例如，Office 2000 提供 mso9.dll 并 OfficeXP 提供 mso.dll 有关的问题。 此代码从 stdafx.h 简化：

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

在此示例中实际使用的类型库中的唯一信息是单词的 CLSID`Application`对象和接口的 IID`ApplicationEvents`接口。 仅在编译时使用此信息。

下面的代码所示 Simple.h。 通过注释记录了相关代码：

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

下面的代码是从 Simple.cpp:

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>请参阅

[事件处理](../atl/event-handling-and-atl.md)<br/>
[ATLEventHandling 示例](../overview/visual-cpp-samples.md)
