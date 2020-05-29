---
title: 匹配事件
description: C++生成见解 SDK 匹配事件函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c60653641c676716bcdd60865433773da79325f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323859"
---
# <a name="matchevent"></a>匹配事件

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`MatchEvent`函数用于将事件与事件类型列表匹配。 如果事件与列表中的类型匹配，则该事件将转发到处理程序以进行进一步处理。

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
要匹配的剩余事件类型。

*可调用*\
支持`operator()`的类型。 有关哪些参数传递给此运算符的详细信息，请参阅*可调用*参数说明。

*TExtraArgs*\
传递给 的额外参数的类型`MatchEvent`。

*事件*\
要与*TEvent*和*TEvents*描述的事件类型匹配的事件。

*调用*\
`MatchEvent`在成功将事件与*TEvent*和*TEvent*描述的任何事件类型匹配后*调用可调用*。 传递给*可调用*的第一个参数是匹配事件类型的 r 值。 在*可调用*的剩余参数中，*额外的Args*参数包是完美的转发。  

*额外阿格*\
与匹配的事件类型一起被完全转发到*可调用*的参数。

### <a name="return-value"></a>返回值

如果匹配成功，则为**true**的**bool**值，否则为**false。**

## <a name="remarks"></a>备注

用于*TEvent*和*TEvents*参数的事件类型是从*捕获类*列表中选择的。 有关可用于匹配的事件和捕获类的列表，请参阅[事件表](../event-table.md)。

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
