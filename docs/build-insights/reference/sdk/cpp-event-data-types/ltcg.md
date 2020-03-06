---
title: LTCG 类
description: C++ BUILD INSIGHTS SDK LTCG 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LTCG
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8e75795e46d64752fd4d1a643585cf6f131cb096
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334672"
---
# <a name="ltcg-class"></a>LTCG 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`LTCG` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[LTCG](../event-table.md#ltcg)事件。

## <a name="syntax"></a>语法

```cpp
class LTCG : public Activity
{
public:
    LTCG(const RawEvent& event);
};
```

## <a name="members"></a>Members

除了其[活动](activity.md)基类的继承成员以外，`LTCG` 类包含以下成员：

### <a name="constructors"></a>构造函数

[LTCG](#ltcg)

## <a name="ltcg"></a>LTCG

```cpp
LTCG(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
一个[LTCG](../event-table.md#ltcg)事件。

::: moniker-end
