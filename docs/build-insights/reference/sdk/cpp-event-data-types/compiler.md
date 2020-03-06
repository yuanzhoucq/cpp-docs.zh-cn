---
title: 编译器类
description: C++生成见解 SDK 编译器类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a63a0bad1ab6063d5986fec77b5135f500ded1ce
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334942"
---
# <a name="compiler-class"></a>编译器类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`Compiler` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[编译器](../event-table.md#compiler)事件。

## <a name="syntax"></a>语法

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Members

除了从其[调用](invocation.md)基类继承的成员以外，`Compiler` 类包含以下成员：

### <a name="constructors"></a>构造函数

[编译程序](#compiler)

## <a name="compiler"></a>编译程序

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[编译器](../event-table.md#compiler)事件。

::: moniker-end
