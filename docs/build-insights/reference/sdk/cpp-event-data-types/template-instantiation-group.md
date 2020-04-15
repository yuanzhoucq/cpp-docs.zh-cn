---
title: 模板即时组类
description: C++生成见解 SDK 模板即时组类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 18dd48219c7c68ce152c381eb505fe37b19ec8dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324263"
---
# <a name="templateinstantiationgroup-class"></a>模板即时组类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`TemplateInstantiationGroup`类与[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackIn会员函数一](../functions/match-event-stack-in-member-function.md)起使用。 使用它匹配[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件组。

## <a name="syntax"></a>语法

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>成员

除了从[事件组\<模板实例化\>](event-group.md)基类继承的成员一起，`TemplateInstantiationGroup`该类包含以下成员：

### <a name="constructors"></a>构造函数

[模板即时组](#template-instantiation-group)

## <a name="templateinstantiationgroup"></a><a name="template-instantiation-group"></a>模板即时组

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>参数

*组*\
一组[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件。

::: moniker-end
