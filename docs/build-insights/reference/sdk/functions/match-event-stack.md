---
title: 匹配事件堆栈
description: C++生成见解 SDK 匹配事件堆栈函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a223d420e8c48667fbd1c6569f02d0486f597b5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323878"
---
# <a name="matcheventstack"></a>匹配事件堆栈

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`MatchEventStack`函数用于将事件堆栈与特定事件层次结构匹配。 匹配的层次结构将转发到处理程序以进行进一步处理。 要了解有关事件、事件堆栈和层次结构的更多信息，请参阅[事件表](../event-table.md)。

## <a name="syntax"></a>语法

```cpp
template <
    typename          TEvent,
    typename...       TEvents,
    typename          TCallable,
    typename...       TExtraArgs>
bool MatchEventStack(
    const EventStack& eventStack,
    TCallable&&       callable,
    TExtraArgs&&...   extraArgs);
```

### <a name="parameters"></a>参数

*TEvent*\
要在事件堆栈中匹配的父项的类型。

*TEvents*\
您希望在事件堆栈中匹配的剩余类型。

*可调用*\
支持`operator()`的类型。 有关哪些参数传递给此运算符的详细信息，请参阅*可调用*参数说明。

*TExtraArgs*\
传递给 的额外参数的类型`MatchEventStack`。

*事件堆栈*\
要与*TEvent*和*TEvents*描述的事件类型层次结构匹配的事件堆栈。

*调用*\
成功将事件堆栈与*TEvent*和*TEvent*描述的事件类型层次结构`MatchEventStack`匹配后，将调用*可调用*。 它将事件层次结构中每种类型的*可调用*一个 r 值参数传递给。 在*可调用*的剩余参数中，*额外的Args*参数包是完美的转发。

*额外阿格*\
与匹配的事件类型一起被完全转发到*可调用*的参数。

### <a name="return-value"></a>返回值

如果匹配成功，则**为 true**的**bool**值，否则为**false。**

## <a name="remarks"></a>备注

*事件堆栈*中的最后一个事件始终与串联\[ *TEvent、TEvents...* *TEvents...*\]类型列表。 所有其他*TEvent*和*TEvents*条目可以匹配*事件堆栈*中的任何位置，但最后一个位置除外，前提是它们的顺序相同。

用于*TEvent*和*TEvents*参数的事件类型是从*捕获类*列表中选择的。 有关可用于匹配的事件和捕获类的列表，请参阅[事件表](../event-table.md)。

## <a name="example"></a>示例

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStack<Compiler, BackEndPass, C2DLL,
                CodeGeneration, Thread, Function>(
        eventStack, [](Compiler cl, BackEndPass bep, C2DLL c2,
            CodeGeneration cg, Thread t, Function f){ /* Do something ... */ });

    bool b2 = MatchEventStack<Compiler, Function>(
        eventStack, [](Compiler cl, Function f){ /* Do something... */ });

    bool b3 = MatchEventStack<Thread, Compiler, Function>(
        eventStack, [](Thread t, Compiler cl Function f){ /* Do something... */ });

    bool b4 = MatchEventStack<Compiler>(
        eventStack, [](Compiler cl){ /* Do something... */ });


    // b1: true because the list of types matches the eventStack exactly.
    // b2: true because Function is the last entry in both the type list
    //     and 'eventStack', and also because Compiler comes before
    //     Function in 'eventStack' and in the type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', they aren't listed in the
    //     right order in the type list.
    // b4: false because the last entry in the type list is Compiler,
    //     which doesn't match the last entry in 'eventStack' (Function).
}
```

::: moniker-end
