---
title: 编译器Pass 类
description: C++生成见解 SDK 编译器传递类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 11af981b647d5183f88dad024d90c0ef4f8a28bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325046"
---
# <a name="compilerpass-class"></a>编译器Pass 类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`CompilerPass`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[BACK_END_PASS](../event-table.md#back-end-pass)或[FRONT_END_PASS](../event-table.md#front-end-pass)事件。

## <a name="syntax"></a>语法

```cpp
class CompilerPass : public Activity
{
public:
    enum class PassCode
    {
        FRONT_END,
        BACK_END
    };

    CompilerPass(const RawEvent& event);

    PassCode       PassCode() const;
    const wchar_t* InputSourcePath() const;
    const wchar_t* OutputObjectPath() const;
};
```

## <a name="members"></a>成员

除了从[其活动](activity.md)基类继承的成员外，`CompilerPass`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[编译器通行证](#compiler-pass)

### <a name="enums"></a>枚举

#### <a name="passcode"></a>密码

|||
|-|-|
|FRONT_END|前端通道。|
|BACK_END|后端传递。|

### <a name="functions"></a>函数

[输入源路径](#input-source-path)\
[输出对象路径](#output-object-path)\
[密码](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a>编译器通行证

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[BACK_END_PASS](../event-table.md#back-end-pass)或[FRONT_END_PASS](../event-table.md#front-end-pass)事件。

## <a name="inputsourcepath"></a><a name="input-source-path"></a>输入源路径

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>返回值

此编译器处理的输入源文件的绝对路径通过。

## <a name="outputobjectpath"></a><a name="output-object-path"></a>输出对象路径

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>返回值

此编译器生成的输出对象文件的绝对路径通过。

## <a name="passcode"></a><a name="pass-code"></a>密码

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>返回值

指示哪个编译器传递由此编译器Pass 对象表示的代码。

::: moniker-end
