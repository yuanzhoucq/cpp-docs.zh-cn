---
title: InvocationGroup 类
description: C++ BUILD Insights SDK InvocationGroup 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b9a2bbcd2b7649b9b5703adc08ed41b272e10276
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334750"
---
# <a name="invocationgroup-class"></a>InvocationGroup 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`InvocationGroup` 类与[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数结合使用。 用于匹配包含[编译器](../event-table.md#compiler)和[链接器](../event-table.md#linker)事件组合的组。

## <a name="syntax"></a>语法

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Members

除了其 EventGroup 中的继承成员[\<调用\>](event-group.md)基类，`InvocationGroup` 类包含以下成员：

### <a name="constructors"></a>构造函数

[InvocationGroup](#invocation-group)

## <a name="invocation-group"></a>InvocationGroup

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>参数

*组*\
包含[编译器](../event-table.md#compiler)和[链接器](../event-table.md#linker)事件的组合的组。

::: moniker-end
