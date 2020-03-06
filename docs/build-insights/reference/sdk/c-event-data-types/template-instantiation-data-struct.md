---
title: TEMPLATE_INSTANTIATION_DATA 结构
description: C++生成见解 SDK TEMPLATE_INSTANTIATION_DATA 结构参考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa669d715dbe56ce7e889330f46f307f520710f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335080"
---
# <a name="template_instantiation_data-structure"></a>TEMPLATE_INSTANTIATION_DATA 结构

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`TEMPLATE_INSTANTIATION_DATA` 结构描述了模板实例化。

## <a name="syntax"></a>语法

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `SpecializationSymbolKey` | 模板专用化的类型的键。 此值在要分析的跟踪中是唯一的。 |
| `PrimaryTemplateSymbolKey` | 专用模板类型的键。 此值在要分析的跟踪中是唯一的。 |
| `KindCode` | 模板实例化的类型。 有关详细信息，请参阅[TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md)。 |

## <a name="remarks"></a>备注

`TEMPLATE_INSTANTIATION_DATA` 结构中的键在要分析的跟踪中是唯一的。 但是，来自不同编译器前端传递的两个不同的密钥可能指向两个相同的类型。 使用来自多个编译器前端传递 `TEMPLATE_INSTANTIATION_DATA` 的信息时，请使用[SYMBOL_NAME](../event-table.md#symbol-name)事件确定两个类型是否相同。 在编译器前端处理结束时，将在完成所有模板实例化之后发出 `SymbolName` 事件。

::: moniker-end
