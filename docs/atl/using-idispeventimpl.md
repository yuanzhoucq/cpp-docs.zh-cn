---
title: 使用 IDispEventImpl (ATL)
ms.date: 08/19/2019
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
ms.openlocfilehash: 9684781ba99d96e2c58d450ee0ff892374e33aef
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630601"
---
# <a name="using-idispeventimpl"></a>使用 IDispEventImpl

使用`IDispEventImpl`处理事件时, 你将需要:

- 从[IDispEventImpl](../atl/reference/idispeventimpl-class.md)派生类。

- 将事件接收器映射添加到你的类。

- 使用[SINK_ENTRY](reference/composite-control-macros.md#sink_entry)或[SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex)宏向事件接收器映射添加条目。

- 实现您想要处理的方法。

- 建议和 unadvise 事件源。

## <a name="example"></a>示例

下面的示例演示如何处理由 Word `DocumentChange`的**应用程序**对象触发的事件。 此事件在`ApplicationEvents`调度接口上定义为方法。

该示例来自[ATLEventHandling 示例](../overview/visual-cpp-samples.md)。

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

该示例使用`#import`从 Word 的类型库生成所需的标头文件。 如果要将此示例与其他版本的 Word 一起使用, 则必须指定正确的 mso dll 文件。 例如, Office 2000 提供 mso9 和 OfficeXP 提供 mso.dll。 此代码简化了*pch* (Visual Studio 2017 及更早版本中的*stdafx.h* ):

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]

以下代码将出现在 NotSoSimple 中。 相关代码按注释记录:

[!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]

## <a name="see-also"></a>请参阅

[事件处理](../atl/event-handling-and-atl.md)<br/>
[ATLEventHandling 示例](../overview/visual-cpp-samples.md)
