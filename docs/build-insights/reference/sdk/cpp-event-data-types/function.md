---
title: Function 类
description: C++生成见解 SDK 函数类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3ff66119007ed7172fed7e824287ab8617c70973
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334768"
---
# <a name="function-class"></a>Function 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`Function` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[函数](../event-table.md#function)事件。

## <a name="syntax"></a>语法

```cpp
class Function : public Activity
{
public:
    Function(const RawEvent& event);

    const char* Name() const;
};
```

## <a name="members"></a>Members

除了其[活动](activity.md)基类的继承成员以外，`Function` 类包含以下成员：

### <a name="constructors"></a>构造函数

[Function](#function)

### <a name="functions"></a>函数

[Name](#name)

## <a name="function"></a>才能

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[函数](../event-table.md#function)事件。

## <a name="name"></a> 名称

```cpp
const char* Name() const;
```

### <a name="return-value"></a>返回值

以 UTF-8 编码的函数的名称。

::: moniker-end
