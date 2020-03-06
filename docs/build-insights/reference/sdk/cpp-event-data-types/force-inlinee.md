---
title: ForceInlinee 类
description: C++ BUILD Insights SDK ForceInlinee 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7d3cce13601a0b3edbcd2b57664b2d0d94a7d3df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334834"
---
# <a name="forceinlinee-class"></a>ForceInlinee 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`ForceInlinee` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[FORCE_INLINEE](../event-table.md#force-inlinee)事件。

## <a name="syntax"></a>语法

```cpp
class ForceInlinee : public SimpleEvent
{
public:
    ForceInlinee(const RawEvent& event);

    const char*             Name() const;
    const unsigned short&   Size() const;
};
```

## <a name="members"></a>Members

除了其[SimpleEvent](simple-event.md)基类的继承成员以外，`ForceInlinee` 类包含以下成员：

### <a name="constructors"></a>构造函数

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>函数

[名称](#name)
[大小](#size)

## <a name="force-inlinee"></a>ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[FORCE_INLINEE](../event-table.md#force-inlinee)事件。

## <a name="name"></a> 名称

```cpp
const char* Name() const;
```

### <a name="return-value"></a>返回值

以 UTF-8 编码的强制内联函数的名称。

## <a name="size"></a>规格

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>返回值

强制内联函数的大小，作为中间指令计数。

::: moniker-end
