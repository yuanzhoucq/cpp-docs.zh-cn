---
title: 命令行类
description: C++生成见解 SDK 命令行类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b35d688acf06579cc27f2fee053ef58032e204e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325049"
---
# <a name="commandline-class"></a>命令行类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`CommandLine`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[COMMAND_LINE](../event-table.md#command-line)事件。

## <a name="syntax"></a>语法

```cpp
class CommandLine : public SimpleEvent
{
public:
    CommandLine(const RawEvent& event);

    const wchar_t* Value() const;
};
```

## <a name="members"></a>成员

除了其[SimpleEvent](simple-event.md)基类中继承的成员外，`CommandLine`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[命令行](#command-line)

### <a name="functions"></a>函数

[“值”](#value)

## <a name="commandline"></a><a name="command-line"></a>命令行

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[COMMAND_LINE](../event-table.md#command-line)事件。

## <a name="value"></a><a name="value"></a> 值

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>返回值

包含命令行的字符串。 该值\_包括从响应文件和环境变量（如 CL、CL、Link\_和\_LINK\_）获取的参数。

::: moniker-end
