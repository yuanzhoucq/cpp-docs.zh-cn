---
title: CompilerPass 类
description: C++ BUILD Insights SDK CompilerPass 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c2fa1c2c4be8aaf5bec77b383f93a4b033ca8e3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334954"
---
# <a name="compilerpass-class"></a>CompilerPass 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`CompilerPass` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它可匹配[BACK_END_PASS](../event-table.md#back-end-pass)或[FRONT_END_PASS](../event-table.md#front-end-pass)事件。

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

## <a name="members"></a>Members

除了其[活动](activity.md)基类的继承成员以外，`CompilerPass` 类包含以下成员：

### <a name="constructors"></a>构造函数

[CompilerPass](#compiler-pass)

### <a name="enums"></a>枚举

#### <a name="passcode"></a>密码

|||
|-|-|
|FRONT_END|前端通过。|
|BACK_END|后端传递。|

### <a name="functions"></a>函数

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[密码](#pass-code)\

## <a name="compiler-pass"></a>CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[BACK_END_PASS](../event-table.md#back-end-pass)或[FRONT_END_PASS](../event-table.md#front-end-pass)事件。

## <a name="input-source-path"></a>InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>返回值

此编译器传递处理的输入源文件的绝对路径。

## <a name="output-object-path"></a>OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>返回值

此编译器传递的输出对象文件的绝对路径。

## <a name="pass-code"></a>密码

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>返回值

指示此 CompilerPass 对象所表示的编译器传递的代码。

::: moniker-end
