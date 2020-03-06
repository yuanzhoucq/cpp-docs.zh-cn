---
title: MakeDynamicReloggerGroup
description: C++ BUILD Insights SDK MakeDynamicReloggerGroup 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4ad394d3ba2982e7ee4f2a497fef2ea65a3c1769
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334396"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeDynamicReloggerGroup` 函数用于创建动态 relogger 组。 Relogger 组的成员从左到右逐个接收事件，直到处理完跟踪中的所有事件。

## <a name="syntax"></a>语法

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>参数

*reloggers*\
动态 relogger 组中包含的[IRelogger](../other-types/irelogger-class.md)指针的矢量。 这些指针可以是 raw、`std::unique_ptr`或 `std::shared_ptr`。 由于继承关系的原因， [IAnalyzer](../other-types/ianalyzer-class.md)指针也被视为 `IRelogger` 指针。

### <a name="return-value"></a>返回值

动态 relogger 组。 使用**auto**关键字来捕获返回值。

## <a name="remarks"></a>备注

与静态 relogger 组不同，动态 relogger 组的成员在编译时不需要是已知的。 可以在运行时基于程序输入或在编译时未知的其他值选择 relogger 组成员。 与静态 relogger 组不同，动态 relogger 组中的[IRelogger](../other-types/irelogger-class.md)指针具有多态行为，并正确调度虚拟函数调用。 这种灵活性会降低事件处理时间。 当所有 relogger 组成员在编译时已知，并且如果不需要多态行为，请考虑使用静态 relogger 组。 若要使用静态 relogger 组，请改为调用[MakeStaticReloggerGroup](make-static-relogger-group.md) 。

动态 relogger 组可以封装在静态 relogger 组中。 将其地址传递给[MakeStaticReloggerGroup](make-static-relogger-group.md)。 使用此方法将动态 relogger 组传递到仅接受静态 relogger 组的[函数，例如重新进行的重新](relog.md)排列。

::: moniker-end
