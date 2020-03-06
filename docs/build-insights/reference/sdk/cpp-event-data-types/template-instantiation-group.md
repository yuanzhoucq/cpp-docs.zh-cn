---
title: TemplateInstantiationGroup 类
description: C++ BUILD Insights SDK TemplateInstantiationGroup 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 281088b4c6cbd39b2fb7677180a7966b490ec3ac
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334540"
---
# <a name="templateinstantiationgroup-class"></a>TemplateInstantiationGroup 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`TemplateInstantiationGroup` 类与[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数结合使用。 用于匹配[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件组。

## <a name="syntax"></a>语法

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>Members

除了其 EventGroup 中的继承成员[\<TemplateInstantiation\>](event-group.md)基类，`TemplateInstantiationGroup` 类包含以下成员：

### <a name="constructors"></a>构造函数

[TemplateInstantiationGroup](#template-instantiation-group)

## <a name="template-instantiation-group"></a>TemplateInstantiationGroup

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>参数

*组*\
一组[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件。

::: moniker-end
