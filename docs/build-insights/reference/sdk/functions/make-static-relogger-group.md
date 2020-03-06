---
title: MakeStaticReloggerGroup
description: C++ BUILD Insights SDK MakeStaticReloggerGroup 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 06927af89b16d9de1148e555868dd2022c59b171
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334384"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeStaticReloggerGroup` 函数用于创建可传递给函数（如重新[生成）的](relog.md)静态 relogger 组。 Relogger 组的成员从左到右逐个接收事件，直到处理完跟踪中的所有事件。

## <a name="syntax"></a>语法

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>参数

*TReloggerPtrs*\
始终推导此参数。

*reloggers*\
静态 relogger 组中包含的[IRelogger](../other-types/irelogger-class.md)指针的参数包。 这些指针可以是 raw、`std::unique_ptr`或 `std::shared_ptr`。 由于继承关系的原因， [IAnalyzer](../other-types/ianalyzer-class.md)指针也被视为 `IRelogger` 指针。

### <a name="return-value"></a>返回值

静态 relogger 组。 使用**auto**关键字来捕获返回值。

## <a name="remarks"></a>备注

与动态 relogger 组不同，静态 relogger 组的成员在编译时必须是已知的。 此外，静态 relogger 组包含不具有多态行为的[IRelogger](../other-types/irelogger-class.md)指针。 使用静态 relogger 组分析 Windows 事件跟踪（ETW）跟踪时，对 `IRelogger` 接口的调用始终解析为 relogger 组成员直接指向的对象。 这种灵活性损失会导致事件处理速度更快。 如果在编译时无法知道 relogger 组的成员，或者在 `IRelogger` 指针上需要多态行为，请考虑使用动态 relogger 组。 可以改为通过调用[MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)来使用动态 relogger 组。

::: moniker-end
