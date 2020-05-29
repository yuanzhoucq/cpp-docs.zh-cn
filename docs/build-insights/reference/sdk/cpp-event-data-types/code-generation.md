---
title: 代码生成类
description: C++生成见解 SDK 代码生成类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CodeGeneration
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 27149d60cc6970843ef2ecccbaf25472f002e35f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325062"
---
# <a name="codegeneration-class"></a>代码生成类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`CodeGeneration`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[CODE_GENERATION](../event-table.md#code-generation)事件。

## <a name="syntax"></a>语法

```cpp
class CodeGeneration : public Activity
{
public:
    CodeGeneration(const RawEvent& event);
};
```

## <a name="members"></a>成员

除了从[其活动](activity.md)基类继承的成员外，`CodeGeneration`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[代码生成](#code-generation)

## <a name="codegeneration"></a><a name="code-generation"></a>代码生成

```cpp
CodeGeneration(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[CODE_GENERATION](../event-table.md#code-generation)事件。

::: moniker-end
