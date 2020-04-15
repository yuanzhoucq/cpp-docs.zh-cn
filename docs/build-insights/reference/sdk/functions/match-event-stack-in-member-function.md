---
title: 匹配事件堆栈成员函数
description: C++生成见解 SDK 匹配事件Stackin成员函数函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28842a02e7edc2e00266d8c7941798f4ce714ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323884"
---
# <a name="matcheventstackinmemberfunction"></a>匹配事件堆栈成员函数

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`MatchEventStackInMemberFunction`函数用于将事件堆栈与特定事件层次结构匹配，由成员函数的参数列表描述。 匹配的层次结构将转发到成员函数以进行进一步处理。 要了解有关事件、事件堆栈和层次结构的更多信息，请参阅[事件表](../event-table.md)。

## <a name="syntax"></a>语法

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, TExtraParams...),
    TExtraArgs&&...           extraArgs);

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, TExtraParams...),
    TExtraArgs&&...           extraArgs);

// Etc...

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename     T3,
    typename     T4,
    typename     T5,
    typename     T6,
    typename     T7,
    typename     T8,
    typename     T9,
    typename     T10,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, TExtraParams...),
    TExtraArgs&&...           extraArgs);
```

### <a name="parameters"></a>参数

*T接口*\
包含成员函数的类型。

*T返回*\
成员函数的返回类型。

*T1*， ...， *T10*\
描述要匹配的事件层次结构的类型。

*特特帕姆斯*\
成员函数接受的额外参数的类型和事件层次结构类型。

*TExtraArgs*\
传递给 的额外参数的类型`MatchEventStackInMemberFunction`。

*事件堆栈*\
要与 T1 到*T10*描述的事件类型*T10*层次结构匹配的事件堆栈。

*对象Ptr*\
指向调用*成员Func*的对象的指针。

*成员丰奇*\
描述要匹配的事件类型层次结构的成员函数。

*额外阿格*\
与事件类型层次结构参数一起完美转发到*成员Func*的参数。

### <a name="return-value"></a>返回值

如果匹配成功，则**为 true**的**bool**值，否则为**false。**

## <a name="remarks"></a>备注

*事件堆栈*中的最后一个事件始终与要匹配的事件类型层次结构中的最后一个条目匹配。 事件类型层次结构中的所有其他类型的都可以匹配*事件堆栈*中的任何位置，但最后一个位置除外，前提是它们的顺序相同。

用于 T1 到*T10*参数的事件类型是从*T10**捕获类*列表中选择的。 有关可用于匹配的事件和捕获类的列表，请参阅[事件表](../event-table.md)。

## <a name="example"></a>示例

```cpp
void MyClass::Foo1(Compiler cl, BackEndPass bep, C2DLL c2,
    CodeGeneration cg, Thread t, Function f) { }

void MyClass::Foo2(Compiler cl, Function f) { }

void MyClass::Foo3(Thread t, Compiler cl, Function f) { }

void MyClass::Foo4(Compiler cl) { }

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo1);

    bool b2 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo2);

    bool b3 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo3);

    bool b4 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo4);

    // b1: true because the parameter types of Foo1 match the eventStack
    //     exactly.
    // b2: true because Function is the last entry in both the member
    //     function parameter list and 'eventStack', and also because
    //     Compiler comes before Function in 'eventStack' and in the
    //     parameter type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', the member function parameter
    //     list doesn't list them in the right order.
    // b4: false because the last entry in the member function parameter
    //     list is Compiler, which doesn't match the last entry in 'eventStack'
    //     (Function).
}
```

::: moniker-end
