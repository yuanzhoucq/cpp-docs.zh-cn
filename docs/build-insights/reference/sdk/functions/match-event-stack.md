---
title: MatchEventStack
description: C++ BUILD Insights SDK MatchEventStack 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 445c2d00c24da10754d32256de0c691e82b557e1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334360"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventStack` 函数用于匹配事件堆栈与特定事件层次结构。 匹配的层次结构将转发到处理程序以便进一步处理。 若要了解有关事件、事件堆栈和层次结构的详细信息，请参阅[事件表](../event-table.md)。

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
要在事件堆栈中匹配的 eldest 父对象的类型。

*TEvents*\
要在事件堆栈中匹配的其余类型。

*TCallable*\
支持 `operator()`的类型。 有关哪些参数传递到此运算符的详细信息，请参阅可*调用*参数说明。

*TExtraArgs*\
传递给 `MatchEventStack`的额外参数的类型。

*eventStack*\
要与*TEvent*和*TEvents*描述的事件类型层次结构匹配的事件堆栈。

可*调用*\
使用*TEvent*和*TEvents*描述的事件类型层次结构成功匹配事件堆栈后，`MatchEventStack` 调用可*调用*。 它将传递给事件层次结构中每个类型*的一个 r*值自变量。 *ExtraArgs*参数包在可*调用*的其余参数中进行了完美转发。

*extraArgs*\
可与匹配的事件*类型一起实现*完美转发的自变量。

### <a name="return-value"></a>返回值

一个**布尔**值，如果匹配成功，则为**true** ; 否则为**false** 。

## <a name="remarks"></a>备注

*EventStack*中的最后一个事件始终与串联 \[*TEvent*， *TEvents ...* \] 类型列表中的最后一项匹配。 所有其他*TEvent*和*TEvents*条目都可以匹配*eventStack*中除最后一个位置之外的任何位置，前提是它们的顺序相同。

用于*TEvent*和*TEvents*参数的事件类型是从*捕获类*的列表中选择的。 有关可以用来匹配事件的事件列表和捕获类，请参阅[事件表](../event-table.md)。

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
