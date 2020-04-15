---
title: 匹配事件成员函数
description: C++生成见解 SDK 匹配事件成员函数函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 522630da16e3f4a1294316d88140f4bc25dca2c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323901"
---
# <a name="matcheventinmemberfunction"></a>匹配事件成员函数

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`MatchEventInMemberFunction`函数用于将事件与成员函数的第一个参数描述的类型匹配。 匹配的事件将转发到成员函数以进行进一步处理。

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

*T接口*\
包含成员函数的类型。

*T返回*\
成员函数的返回类型。

*TEvent*\
要匹配的事件的类型。

*特特帕姆斯*\
成员函数接受的额外参数的类型以及要匹配的事件类型。

*TExtraArgs*\
传递给 的额外参数的类型`MatchEventInMemberFunction`。

*事件*\
要与*TEvent*描述的事件类型匹配的事件。

*对象Ptr*\
指向调用*成员Func*的对象的指针。

*成员丰奇*\
描述要匹配的事件类型的成员函数。

*额外阿格*\
与事件类型参数一起完美转发到*成员Func*的参数。

### <a name="return-value"></a>返回值

如果匹配成功，则**为 true**的**bool**值，否则为**false。**

## <a name="remarks"></a>备注

可用于*TEvent*参数的事件类型可以从*捕获类*列表中选择。 有关可用于匹配的事件和捕获类的列表，请参阅[事件表](../event-table.md)。

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
