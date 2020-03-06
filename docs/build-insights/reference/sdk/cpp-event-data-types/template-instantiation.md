---
title: TemplateInstantiation 类
description: C++ BUILD Insights SDK TemplateInstantiation 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2c94f8d3a4613e072c03f6dd4c846798d3d2122b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334522"
---
# <a name="templateinstantiation-class"></a>TemplateInstantiation 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`TemplateInstantiation` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件。

## <a name="syntax"></a>语法

```cpp
class TemplateInstantiation : public Activity
{
public:
    enum class Kind
    {
        CLASS       = TEMPLATE_INSTANTIATION_KIND_CODE_CLASS,
        FUNCTION    = TEMPLATE_INSTANTIATION_KIND_CODE_FUNCTION,
        VARIABLE    = TEMPLATE_INSTANTIATION_KIND_CODE_VARIABLE,
        CONCEPT     = TEMPLATE_INSTANTIATION_KIND_CODE_CONCEPT
    };

    TemplateInstantiation(const RawEvent& event);

    const unsigned long long& SpecializationSymbolKey() const;
    const unsigned long long& PrimaryTemplateSymbolKey() const;

    Kind Kind() const;
};
```

## <a name="members"></a>Members

除了其[活动](activity.md)基类的继承成员以外，`TemplateInstantiation` 类包含以下成员：

### <a name="constructors"></a>构造函数

[TemplateInstantiation](#template-instantiation)

### <a name="functions"></a>函数

[Kind](#kind)
[PrimaryTemplateSymbolKey](#primary-template-symbol-key)
[SpecializationSymbolKey](#specialization-symbol-key)

## <a name="kind"></a>好

```cpp
Kind Kind() const;
```

### <a name="return-value"></a>返回值

描述已完成的模板实例化类型的代码。

## <a name="primary-template-symbol-key"></a>PrimaryTemplateSymbolKey

```cpp
const unsigned long long& PrimaryTemplateSymbolKey() const;
```

### <a name="return-value"></a>返回值

专用化的模板类型的数值标识符。 此标识符在编译器前端传递中是唯一的。

## <a name="specialization-symbol-key"></a>SpecializationSymbolKey

```cpp
const unsigned long long& SpecializationSymbolKey() const;
```

### <a name="return-value"></a>返回值

专用化类型的数值标识符。 此标识符在编译器前端传递中是唯一的。

## <a name="template-instantiation"></a>TemplateInstantiation

```cpp
TemplateInstantiation(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件。

::: moniker-end
