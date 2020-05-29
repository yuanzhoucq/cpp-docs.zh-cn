---
title: 调用组类
description: C++生成见解 SDK 调用组类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff5a73d5304a21c314c0fc5ce442e0ffc23b28fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324694"
---
# <a name="invocationgroup-class"></a>调用组类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`InvocationGroup`类与[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackIn会员函数一](../functions/match-event-stack-in-member-function.md)起使用。 使用它匹配包含["编译器](../event-table.md#compiler)"和["链接"](../event-table.md#linker)事件组合的组。

## <a name="syntax"></a>语法

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>成员

除了从[其 EventGroup\<调用\>](event-group.md)基类继承的成员一起，`InvocationGroup`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[调用组](#invocation-group)

## <a name="invocationgroup"></a><a name="invocation-group"></a>调用组

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>参数

*组*\
包含["编译器"](../event-table.md#compiler)和["链接"](../event-table.md#linker)事件组合的组。

::: moniker-end
