---
title: 链接器类
description: C++生成见解 SDK 链接器类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Linker
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bb8948d7772046e18d5db5002deed48d0dd88375
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334708"
---
# <a name="linker-class"></a>链接器类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`Linker` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[链接器](../event-table.md#linker)事件。

## <a name="syntax"></a>语法

```cpp
class Linker : public Invocation
{
public:
    Linker(const RawEvent& event);
};
```

## <a name="members"></a>Members

除了从其[调用](invocation.md)基类继承的成员以外，`Linker` 类包含以下成员：

### <a name="constructors"></a>构造函数

[链接器](#linker)

## <a name="linker"></a>器

```cpp
Linker(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[链接器](../event-table.md#linker)事件。

::: moniker-end
