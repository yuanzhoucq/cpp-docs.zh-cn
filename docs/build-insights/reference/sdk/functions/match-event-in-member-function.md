---
title: MatchEventInMemberFunction
description: C++ BUILD Insights SDK MatchEventInMemberFunction 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eabbb8a91609b1447ebcc19af32df2ffed347c24
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334378"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventInMemberFunction` 函数用于将事件与成员函数第一个参数所描述的类型进行匹配。 匹配的事件将转发到成员函数以便进一步处理。

## <a name="syntax"></a>语法

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     TEvent,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventInMemberFunction(
    const RawEvent&          event,
    TInterface*              objectPtr,
    TReturn (TInterface::*   memberFunc)(TEvent, TExtraParams...),
    TExtraArgs&&...          extraArgs);
```

### <a name="parameters"></a>参数

*TInterface*\
包含成员函数的类型。

*TReturn*\
成员函数的返回类型。

*TEvent*\
要匹配的事件类型。

*TExtraParams*\
成员函数接受的额外参数的类型，以及要匹配的事件类型。

*TExtraArgs*\
传递给 `MatchEventInMemberFunction`的额外参数的类型。

*event*\
要与*TEvent*描述的事件类型匹配的事件。

*objectPtr*\
指向对象的指针，该对象在其上调用*memberFunc* 。

*memberFunc*\
描述要匹配的事件类型的成员函数。

*extraArgs*\
可完美转发到*memberFunc*以及事件类型参数的参数。

### <a name="return-value"></a>返回值

一个**布尔**值，如果匹配成功，则为**true** ; 否则为**false** 。

## <a name="remarks"></a>备注

可从*捕获类*的列表中选择要用于*TEvent*参数的事件类型。 有关可以用来匹配事件的事件列表和捕获类，请参阅[事件表](../event-table.md)。

## <a name="example"></a>示例

```cpp
void MyClass::Foo1(Function f) {}

void MyClass::Foo2(Compiler cl) {}

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo1);

    bool b2 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo2);

    // b1: true because the first parameter of Foo1 is Function.
    // b2: false because the first parameter of Foo2 isn't Function.
}
```

::: moniker-end
