---
title: MatchEventStack
description: C++ Build Insights SDK MatchEventStack 函数参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae476c402c3ea0cad558ce41a979b4233e0f1dd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224118"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

C++ Build Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio“版本”选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面上目录表的顶部。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventStack` 函数用于将事件堆栈与特定的事件层次结构进行匹配。 匹配的层次结构被转发给处理程序，以供进一步处理。 若要详细了解事件、事件堆栈和层次结构，请参阅[事件表](../event-table.md)。

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

TEvent\
要在事件堆栈中匹配的最旧父事件的类型。

TEvents\
要在事件堆栈中匹配的其余类型。

TCallable\
支持 `operator()` 的类型。 若要详细了解哪些参数传递给此运算符，请参阅 callable 参数说明。

TExtraArgs\
传递给 `MatchEventStack` 的额外参数的类型。

eventStack\
要与 TEvent 和 TEvents 描述的事件类型层次结构进行匹配的事件堆栈。

callable\
在成功地将事件堆栈与 TEvent 和 TEvents 描述的事件类型层次结构进行匹配后，`MatchEventStack` 调用 callable。 它将事件层次结构中每个类型的一个右值参数传递给 callable。 extraArgs 参数包在 callable 的其余参数中是完美转发的。

extraArgs\
与匹配的事件类型一起完美转发给 callable 的参数。

### <a name="return-value"></a>返回值

如果匹配成功，则 `bool` 值为 `true`；否则，值为 `false`。

## <a name="remarks"></a>备注

eventStack 中的最后一个事件始终与连接的 \[TEvent, TEvents...\] 类型列表中的最后一个条目进行匹配。 其他所有 TEvent 和 TEvents 条目可以与 eventStack 中的任何位置进行匹配（最后一个除外），前提是它们的顺序相同。

用于 TEvent 和 TEvents 参数的事件类型是从 Capture 类的列表中选择的。 有关事件以及可用于匹配它们的 Capture 类的列表，请参阅[事件表](../event-table.md)。

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
