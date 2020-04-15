---
title: 模板即时化类
description: C++生成见解 SDK 模板即时性类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ba8fd10efc6a536c9160f10b19e19e17bfaaad98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324222"
---
# <a name="templateinstantiation-class"></a>模板即时化类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`TemplateInstantiation`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件。

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

## <a name="members"></a>成员

除了从[其活动](activity.md)基类继承的成员外，`TemplateInstantiation`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[模板即时性](#template-instantiation)

### <a name="functions"></a>函数

[类型](#kind)
[主模板符号密钥](#primary-template-symbol-key)
[专门化符号密钥](#specialization-symbol-key)

## <a name="kind"></a><a name="kind"></a>种类

```cpp
Kind Kind() const;
```

### <a name="return-value"></a>返回值

描述已完成的模板实例化类型的代码。

## <a name="primarytemplatesymbolkey"></a><a name="primary-template-symbol-key"></a>主模板符号键

```cpp
const unsigned long long& PrimaryTemplateSymbolKey() const;
```

### <a name="return-value"></a>返回值

专用模板类型的数值标识符。 此标识符在编译器前端传递中是唯一的。

## <a name="specializationsymbolkey"></a><a name="specialization-symbol-key"></a>专业化符号密钥

```cpp
const unsigned long long& SpecializationSymbolKey() const;
```

### <a name="return-value"></a>返回值

专门化类型的数值标识符。 此标识符在编译器前端传递中是唯一的。

## <a name="templateinstantiation"></a><a name="template-instantiation"></a>模板即时性

```cpp
TemplateInstantiation(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件。

::: moniker-end
