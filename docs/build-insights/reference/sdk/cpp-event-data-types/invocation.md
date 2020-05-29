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
ms.openlocfilehash: fcb087d46ea445251b0108f811545a44c26f421e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324641"
---
# <a name="invocation-class"></a>调用类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`Invocation`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配["编译器](../event-table.md#compiler)"或["链接"](../event-table.md#linker)事件。

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

## <a name="members"></a>成员

除了从[其活动](activity.md)基类继承的成员外，`Invocation`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[调用](#invocation)

### <a name="functions"></a>函数

[工具路径](#tool-path)
[工具版本](#tool-version)
[版本字符串](#tool-version-string)
[类型工作](#type)
[目录](#working-directory)

## <a name="invocation"></a><a name="invocation"></a>调用

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[一个编译器](../event-table.md#compiler)或[链接器](../event-table.md#linker)事件。

## <a name="toolpath"></a><a name="tool-path"></a>工具路径

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>返回值

调用的工具的绝对路径。

## <a name="toolversion"></a><a name="tool-version"></a>工具版本

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>返回值

作为[INVOCATION_VERSION_DATA引用](../c-event-data-types/invocation-version-data-struct.md)而调用的工具的版本。

## <a name="toolversionstring"></a><a name="tool-version-string"></a>工具版本字符串

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>返回值

作为 ANSI 字符串调用的工具的版本。

## <a name="type"></a><a name="type"></a> 类型

```cpp
Type Type() const;
```

### <a name="return-value"></a>返回值

指示被调用工具的代码。

## <a name="workingdirectory"></a><a name="working-directory"></a>工作目录

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>返回值

调用工具的目录的绝对路径。

::: moniker-end
