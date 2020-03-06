---
title: FrontEndFileGroup 类
description: C++ BUILD Insights SDK FrontEndFileGroup 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 343a5a0d798d6c719088bd49668e70b10fba6d1a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334828"
---
# <a name="frontendfilegroup-class"></a>FrontEndFileGroup 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`FrontEndFileGroup` 类与[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数结合使用。 用于匹配[FRONT_END_FILE](../event-table.md#front-end-file)事件组。

## <a name="syntax"></a>语法

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>Members

除了其 EventGroup 中的继承成员[\<FrontEndFile\>](event-group.md)基类，`FrontEndFileGroup` 类包含以下成员：

### <a name="constructors"></a>构造函数

[FrontEndFileGroup](#front-end-file-group)

## <a name="front-end-file-group"></a>FrontEndFileGroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>参数

*组*\
一组[FRONT_END_FILE](../event-table.md#front-end-file)事件。

::: moniker-end
