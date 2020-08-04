---
title: MatchEvent
description: C++ Build Insights SDK MatchEvent 函数参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8ec2c6bfcacf28998058dc66b5f363fbf1ea5d70
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224105"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

C++ Build Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio“版本”选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面上目录表的顶部。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEvent` 函数用于将事件与事件类型列表进行匹配。 如果事件与列表中的类型匹配，则会转发给处理程序，以供进一步处理。

## <a name="syntax"></a>语法

```cpp
template <
    typename        TEvent,
    typename...     TEvents,
    typename        TCallable,
    typename...     TExtraArgs>
bool MatchEvent(
    const RawEvent& event,
    TCallable&&     callable,
    TExtraArgs&&... extraArgs);
```

### <a name="parameters"></a>参数

TEvent\
要匹配的第一个事件类型。

TEvents\
要匹配的其余事件类型。

TCallable\
支持 `operator()` 的类型。 若要详细了解哪些参数传递给此运算符，请参阅 callable 参数说明。

TExtraArgs\
传递给 `MatchEvent` 的额外参数的类型。

*event*\
要与 TEvent 和 TEvents 描述的事件类型进行匹配的事件。

callable\
在成功地将事件与 TEvent 和 TEvents 描述的任何事件类型进行匹配后，`MatchEvent` 调用 callable。 传递给 callable 的第一个参数是匹配的事件类型的右值。 extraArgs 参数包在 callable 的其余参数中是完美转发的。  

extraArgs\
与匹配的事件类型一起完美转发给 callable 的参数。

### <a name="return-value"></a>返回值

如果匹配成功，则 `bool` 值为 `true`；否则，值为 `false`。

## <a name="remarks"></a>备注

用于 TEvent 和 TEvents 参数的事件类型是从 Capture 类的列表中选择的。 有关事件以及可用于匹配它们的 Capture 类的列表，请参阅[事件表](../event-table.md)。

## <a name="example"></a>示例

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEvent<Function, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});

    bool b2 = MatchEvent<CodeGeneration, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});


    // b1: true because the list of types contains Function, which is
    //     the type of the event we are trying to match.
    // b2: false because the list of types doesn't contain Function.
}
```

::: moniker-end
