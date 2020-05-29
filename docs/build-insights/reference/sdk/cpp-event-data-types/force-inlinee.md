---
title: 力内联类
description: C++构建见解 SDK 强制内联类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c6a1af0384197a0a3b6062ad9ef30537c348190d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324786"
---
# <a name="forceinlinee-class"></a>力内联类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`ForceInlinee`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[FORCE_INLINEE](../event-table.md#force-inlinee)事件。

## <a name="syntax"></a>语法

```cpp
class ForceInlinee : public SimpleEvent
{
public:
    ForceInlinee(const RawEvent& event);

    const char*             Name() const;
    const unsigned short&   Size() const;
};
```

## <a name="members"></a>成员

除了其[SimpleEvent](simple-event.md)基类中继承的成员外，`ForceInlinee`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[力因内](#force-inlinee)

### <a name="functions"></a>函数

[名称](#name)
[大小](#size)

## <a name="forceinlinee"></a><a name="force-inlinee"></a>力因内

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[FORCE_INLINEE](../event-table.md#force-inlinee)事件。

## <a name="name"></a><a name="name"></a>名字

```cpp
const char* Name() const;
```

### <a name="return-value"></a>返回值

力内联函数的名称，在 UTF-8 中编码。

## <a name="size"></a><a name="size"></a> 大小

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>返回值

力内联函数的大小，作为中间指令计数。

::: moniker-end
