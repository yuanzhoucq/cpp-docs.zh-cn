---
title: Lib输出类
description: C++生成见解 SDK LibOutput 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fda7b471759a9c49937214bb2176473226668776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324625"
---
# <a name="liboutput-class"></a>Lib输出类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`LibOutput`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[LIB_OUTPUT](../event-table.md#lib-output)事件。

## <a name="syntax"></a>语法

```cpp
class LibOutput : public FileOutput
{
public:
    LibOutput(const RawEvent& event);
};
```

## <a name="members"></a>成员

除了从[FileOutput](file-output.md)基类继承的成员一起，`LibOutput`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[Lib输出](#lib-output)

## <a name="liboutput"></a><a name="lib-output"></a>Lib输出

```cpp
LibOutput(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[LIB_OUTPUT](../event-table.md#lib-output)事件。

::: moniker-end
