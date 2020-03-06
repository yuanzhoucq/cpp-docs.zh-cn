---
title: Value 类
description: C++ BUILD Insights SDK value 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 19e9278e76fb2116dac30a0e790fba86c6c56484
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334924"
---
# <a name="environmentvariable-class"></a>Value 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`EnvironmentVariable` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)事件。

## <a name="syntax"></a>语法

```cpp
class EnvironmentVariable : public SimpleEvent
{
public:
    EnvironmentVariable(const RawEvent& event);

    const wchar_t* Name() const;
    const wchar_t* Value() const;
};
```

## <a name="members"></a>Members

除了其[SimpleEvent](simple-event.md)基类的继承成员以外，`EnvironmentVariable` 类包含以下成员：

### <a name="constructors"></a>构造函数

[Value](#environment-variable)

### <a name="functions"></a>函数

[Name](#name)
[Value](#value)

## <a name="environment-variable"></a>Value

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)事件。

## <a name="name"></a> 名称

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>返回值

环境变量的名称。

## <a name="value"></a>负值

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>返回值

环境变量的值。

::: moniker-end
