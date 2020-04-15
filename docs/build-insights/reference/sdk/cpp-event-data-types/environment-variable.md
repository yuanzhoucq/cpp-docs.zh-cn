---
title: 环境变量类
description: C++生成见解 SDK 环境变量类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 963c52e0ea9e048448c6f2b3ac62d9938817467e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325021"
---
# <a name="environmentvariable-class"></a>环境变量类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`EnvironmentVariable`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)事件。

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

## <a name="members"></a>成员

除了其[SimpleEvent](simple-event.md)基类中继承的成员外，`EnvironmentVariable`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>函数

[名称](#name)
[值](#value)

## <a name="environmentvariable"></a><a name="environment-variable"></a>环境变量

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)事件。

## <a name="name"></a><a name="name"></a>名字

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>返回值

环境变量的名称。

## <a name="value"></a><a name="value"></a> 值

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>返回值

环境变量的值。

::: moniker-end
