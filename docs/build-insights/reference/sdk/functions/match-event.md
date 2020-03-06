---
title: MatchEvent
description: C++ BUILD Insights SDK MatchEvent 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f8022953e2f56f7c8917f161b094c50e0c5ecbdf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334354"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEvent` 函数用于匹配事件类型列表的事件。 如果事件与列表中的类型相匹配，则会将其转发到处理程序以供进一步处理。

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

*TEvent*\
要匹配的第一个事件类型。

*TEvents*\
要匹配的其余事件类型。

*TCallable*\
支持 `operator()`的类型。 有关哪些参数传递到此运算符的详细信息，请参阅可*调用*参数说明。

*TExtraArgs*\
传递给 `MatchEvent`的额外参数的类型。

*event*\
要与*TEvent*和*TEvents*描述的事件类型匹配的事件。

可*调用*\
`MatchEvent` 在将事件与*TEvent*和*TEvents*描述的任何事件类型成功匹配后，调用可*调用*。 传递给可*调用*的第一个参数是匹配的事件类型的 r 值。 *ExtraArgs*参数包在可*调用*的其余参数中进行了完美转发。  

*extraArgs*\
可与匹配的事件*类型一起实现*完美转发的自变量。

### <a name="return-value"></a>返回值

如果匹配成功，则为**true**的**布尔**值; 否则为**false** 。

## <a name="remarks"></a>备注

用于*TEvent*和*TEvents*参数的事件类型是从*捕获类*的列表中选择的。 有关可以用来匹配事件的事件列表和捕获类，请参阅[事件表](../event-table.md)。

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
