---
title: 自下而上类
description: C++生成见解 SDK 自下而上类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BottomUp
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1cfe25aaa5736b9e2ba55a577e64958a6b9f113b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325208"
---
# <a name="bottomup-class"></a>自下而上类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`BottomUp`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[BOTTOM_UP](../event-table.md#bottom-up)事件。

## <a name="syntax"></a>语法

```cpp
class BottomUp : public Activity
{
public:
    BottomUp(const RawEvent& event);
};
```

## <a name="members"></a>成员

除了从[其活动](activity.md)基类继承的成员外，`BottomUp`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[自下而上](#bottom-up)

## <a name="bottomup"></a><a name="bottom-up"></a>自下而上

```cpp
BottomUp(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[BOTTOM_UP](../event-table.md#bottom-up)事件。

::: moniker-end
