---
title: TEMPLATE_INSTANTIATION_DATA结构
description: C++构建见解 SDK TEMPLATE_INSTANTIATION_DATA结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a38d19368e7c0a9912907f1da6e7a2e31ffe8d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325331"
---
# <a name="template_instantiation_data-structure"></a>TEMPLATE_INSTANTIATION_DATA结构

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

结构`TEMPLATE_INSTANTIATION_DATA`描述模板实例化。

## <a name="syntax"></a>语法

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>成员

|  |  |
|--|--|
| `SpecializationSymbolKey` | 模板专业化化类型的键。 此值在要分析的跟踪中是唯一的。 |
| `PrimaryTemplateSymbolKey` | 专用主模板类型的键。 此值在要分析的跟踪中是唯一的。 |
| `KindCode` | 模板实例化的类型。 有关详细信息，请参阅[TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md)。 |

## <a name="remarks"></a>备注

结构中的`TEMPLATE_INSTANTIATION_DATA`键在要分析的跟踪中是唯一的。 但是，来自不同编译器前端传递的两个不同的密钥可能指向两种相同的类型。 使用`TEMPLATE_INSTANTIATION_DATA`来自多个编译器前端传递的信息时，请使用[SYMBOL_NAME](../event-table.md#symbol-name)事件来确定两种类型是否相同。 `SymbolName`在编译器前端传递结束时，在进行所有模板实例化后，将发出事件。

::: moniker-end
