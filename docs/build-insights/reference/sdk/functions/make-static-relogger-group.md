---
title: 使静态重新记录组
description: C++生成见解 SDK 使静态重新记录组函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75b638537cb8e0cdeeb5476a3f5277e8e90d9baf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323917"
---
# <a name="makestaticreloggergroup"></a>使静态重新记录组

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`MakeStaticReloggerGroup`函数用于创建一个静态重新记录组，该组可以传递给函数，如[Relog](relog.md)。 重新记录组的成员从左到右逐个接收事件，直到跟踪中的所有事件都得到处理。

## <a name="syntax"></a>语法

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>参数

*TReloggerPtrs*\
始终推导此参数。

*重新记录*\
包含在静态重新记录器组中的[IRelogger](../other-types/irelogger-class.md)指针的参数包。 这些指针可以是生的，`std::unique_ptr`也可以`std::shared_ptr`是 。 [由于继承关系，IAnalyzer](../other-types/ianalyzer-class.md)指针也被视为`IRelogger`指针。

### <a name="return-value"></a>返回值

静态重新记录组。 使用**自动**关键字捕获返回值。

## <a name="remarks"></a>备注

与动态重新记录组不同，静态重新记录组的成员必须在编译时知道。 此外，静态重新记录器组包含没有多态行为的[IRelogger](../other-types/irelogger-class.md)指针。 当使用静态重新记录组分析 Windows （ETW） 跟踪的事件跟踪时，对接口的`IRelogger`调用始终解析为重新记录组成员直接指向的对象。 这种灵活性的丧失具有更快的事件处理时间的可能性。 如果在编译时无法知道重新记录组的成员，或者在`IRelogger`指针上需要多态行为，请考虑使用动态重新记录组。 您可以通过调用[MakeDynamic ReloggerGroup](make-dynamic-relogger-group.md)来使用动态重新记录组。

::: moniker-end
