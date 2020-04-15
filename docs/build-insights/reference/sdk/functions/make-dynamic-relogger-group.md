---
title: 使动态重新记录组
description: C++生成见解 SDK 使动态重新记录组函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f49e37f8e1a8b9ca9a800d20b2891a54453095ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323955"
---
# <a name="makedynamicreloggergroup"></a>使动态重新记录组

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`MakeDynamicReloggerGroup`函数用于创建动态重新记录组。 重新记录组的成员从左到右逐个接收事件，直到跟踪中的所有事件都得到处理。

## <a name="syntax"></a>语法

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>参数

*重新记录*\
动态[重新记录组中包含的 IRelogger](../other-types/irelogger-class.md)指针的矢量。 这些指针可以是生的，`std::unique_ptr`也可以`std::shared_ptr`是 。 [由于继承关系，IAnalyzer](../other-types/ianalyzer-class.md)指针也被视为`IRelogger`指针。

### <a name="return-value"></a>返回值

动态重新记录组。 使用**自动**关键字捕获返回值。

## <a name="remarks"></a>备注

与静态重新记录组不同，动态重新记录组的成员不需要在编译时已知。 您可以根据程序输入或在运行时根据编译时未知的其他值选择重新记录组成员。 与静态重新记录器组不同，动态重新记录器组中的[IRelogger](../other-types/irelogger-class.md)指针具有多态行为，并且虚拟函数调用正确调度。 这种灵活性的代价可能是较慢的事件处理时间。 当所有重新记录组成员在编译时都已知，并且不需要多态行为时，请考虑使用静态重新记录组。 要使用静态重新记录组，请改为调用[MakeStaticReloggerGroup。](make-static-relogger-group.md)

动态重新记录器组可以封装在静态重新记录器组中。 你通过它的地址[，使静态重新记录组](make-static-relogger-group.md)。 使用此技术将动态重新记录器组传递给函数，如[Relog](relog.md)，该函数仅接受静态重新记录组。

::: moniker-end
