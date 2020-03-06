---
title: LinkerPass 类
description: C++ BUILD Insights SDK LinkerPass 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 49a46b57d82391f4c253128c14b1b81d52945eae
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334720"
---
# <a name="linkerpass-class"></a>LinkerPass 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`LinkerPass` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 用于匹配[pass1.log](../event-table.md#pass1)或[PASS2](../event-table.md#pass2)事件。

## <a name="syntax"></a>语法

```cpp
class LinkerPass : public Activity
{
public:
    LinkerPass(const RawEvent& event);
};
```

## <a name="members"></a>Members

除了其[活动](activity.md)基类的继承成员以外，`LinkerPass` 类包含以下成员：

### <a name="constructors"></a>构造函数

[LinkerPass](#linker-pass)

## <a name="linker-pass"></a>LinkerPass

```cpp
LinkerPass(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[Pass1.log](../event-table.md#pass1)或[PASS2](../event-table.md#pass2)事件。

::: moniker-end
