---
title: 调用类
description: C++生成见解 SDK 调用类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c4698300a3eeaf77210ad74f84b0c0cd219b457
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334744"
---
# <a name="invocation-class"></a>调用类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`Invocation` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 用于匹配[编译器](../event-table.md#compiler)或[链接器](../event-table.md#linker)事件。

## <a name="syntax"></a>语法

```cpp
class Invocation : public Activity
{
    const INVOCATION_DATA* data_;

public:
    enum class Type
    {
        CL      = MSVC_TOOL_CODE_CL,
        LINK    = MSVC_TOOL_CODE_LINK
    };

    Invocation(const RawEvent& event);

    Type             Type() const;
    const char*      ToolVersionString() const;
    const wchar_t*   WorkingDirectory() const;
    const wchar_t*   ToolPath() const;

    const INVOCATION_VERSION_DATA& ToolVersion() const;
};
```

## <a name="members"></a>Members

除了其[活动](activity.md)基类的继承成员以外，`Invocation` 类包含以下成员：

### <a name="constructors"></a>构造函数

[调用](#invocation)

### <a name="functions"></a>函数

[刀具路径](#tool-path)
[ToolVersion](#tool-version)
[ToolVersionString](#tool-version-string)
[类型](#type)
[WorkingDirectory](#working-directory)

## <a name="invocation"></a>调用

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[编译器](../event-table.md#compiler)或[链接器](../event-table.md#linker)事件。

## <a name="tool-path"></a>ToolPath

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>返回值

调用的工具的绝对路径。

## <a name="tool-version"></a>ToolVersion

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>返回值

作为[INVOCATION_VERSION_DATA](../c-event-data-types/invocation-version-data-struct.md)引用被调用的工具的版本。

## <a name="tool-version-string"></a>ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>返回值

作为 ANSI 字符串调用的工具的版本。

## <a name="type"></a>类别

```cpp
Type Type() const;
```

### <a name="return-value"></a>返回值

指示已调用的工具的代码。

## <a name="working-directory"></a>WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>返回值

调用此工具的目录的绝对路径。

::: moniker-end
