---
title: LinkerGroup 类
description: C++ BUILD Insights SDK LinkerGroup 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 95b0dcc3a771ec07ee60185a79a5ddbc29434b5d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334726"
---
# <a name="linkergroup-class"></a>LinkerGroup 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`LinkerGroup` 类与[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数结合使用。 使用它匹配[链接器](../event-table.md#linker)事件的组。

## <a name="syntax"></a>语法

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Members

除了其 EventGroup 中的继承成员[\<链接器\>](event-group.md)基类以外，`LinkerGroup` 类包含以下成员：

### <a name="constructors"></a>构造函数

[LinkerGroup](#linker-group)

## <a name="linker-group"></a>LinkerGroup

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>参数

*组*\
一组[链接器](../event-table.md#linker)事件。

::: moniker-end
