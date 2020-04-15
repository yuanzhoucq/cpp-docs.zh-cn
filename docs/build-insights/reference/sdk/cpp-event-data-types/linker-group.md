---
title: 链接器组类
description: C++生成见解 SDK 链接器组类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c59d62938e5bd7b839ad12a321a03510e708e0fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324647"
---
# <a name="linkergroup-class"></a>链接器组类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`LinkerGroup`类与[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackIn会员函数一](../functions/match-event-stack-in-member-function.md)起使用。 使用它匹配[LINKER](../event-table.md#linker)事件组。

## <a name="syntax"></a>语法

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>成员

除了从[其 EventGroup\<Linker\>](event-group.md)基类继承的成员一起，`LinkerGroup`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[链接器组](#linker-group)

## <a name="linkergroup"></a><a name="linker-group"></a>链接器组

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>参数

*组*\
一组[LINKER](../event-table.md#linker)事件。

::: moniker-end
