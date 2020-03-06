---
title: 命令行类
description: C++生成见解 SDK 命令行引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff16646920fe77f7f3b4cb8a194a38984c3e6c32
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334984"
---
# <a name="commandline-class"></a>命令行类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`CommandLine` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[COMMAND_LINE](../event-table.md#command-line)事件。

## <a name="syntax"></a>语法

```cpp
class CommandLine : public SimpleEvent
{
public:
    CommandLine(const RawEvent& event);

    const wchar_t* Value() const;
};
```

## <a name="members"></a>Members

除了其[SimpleEvent](simple-event.md)基类的继承成员以外，`CommandLine` 类包含以下成员：

### <a name="constructors"></a>构造函数

[行为](#command-line)

### <a name="functions"></a>函数

[值](#value)

## <a name="command-line"></a>行为

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[COMMAND_LINE](../event-table.md#command-line)事件。

## <a name="value"></a>负值

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>返回值

包含命令行的字符串。 此值包括从响应文件中获取的参数，以及来自 CL、\_CL\_、Link 和 \_链接\_的环境变量。

::: moniker-end
