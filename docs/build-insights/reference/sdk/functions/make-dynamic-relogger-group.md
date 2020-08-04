---
title: MakeDynamicReloggerGroup
description: C++ Build Insights SDK MakeDynamicReloggerGroup 函数参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c0d1348be8878e686aeba4a58c407264264c5bc4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224183"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

C++ Build Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio“版本”选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面上目录表的顶部。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeDynamicReloggerGroup` 函数用于创建动态 relogger 组。 relogger 组的成员从左到右逐个接收事件，直到处理完跟踪中的所有事件为止。

## <a name="syntax"></a>语法

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>参数

reloggers\
动态 relogger 组中包含的 [IRelogger](../other-types/irelogger-class.md) 指针的矢量。 这些指针可以是 raw、`std::unique_ptr` 或 `std::shared_ptr`。 由于继承关系，[IAnalyzer](../other-types/ianalyzer-class.md) 指针也被认为是 `IRelogger` 指针。

### <a name="return-value"></a>返回值

动态 relogger 组。 使用 `auto` 关键字来捕获返回值。

## <a name="remarks"></a>备注

与静态 relogger 组不同，动态 relogger 组的成员在编译时不必是已知的。 可以在运行时根据程序输入或在编译时未知的其他值选择 relogger 组成员。 与静态 relogger 组不同，动态 relogger 组中的 [`IRelogger`](../other-types/irelogger-class.md) 指针有多变行为，并虚拟函数调用被正确地分派。 这种灵活性的代价可能是事件处理速度减慢。 如果所有 relogger 组成员在编译时都是已知的，并且你不需要多变行为，请考虑使用静态 relogger 组。 若要使用静态 relogger 组，请改为调用 [`MakeStaticReloggerGroup`](make-static-relogger-group.md)。

动态 relogger 组可以封装在静态 relogger 组中。 将它的地址传递给 [`MakeStaticReloggerGroup`](make-static-relogger-group.md)。 使用这种技术将动态 relogger 组传递到 [`Relog`](relog.md) 等函数，这些函数只接受静态 relogger 组。

::: moniker-end
