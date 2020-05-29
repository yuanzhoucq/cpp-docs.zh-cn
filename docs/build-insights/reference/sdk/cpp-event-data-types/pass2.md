---
title: Pass2 类
description: C++生成见解 SDK Pass2 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Pass2
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 89b775c60b1d136c33dbaf2c4e39f247be7bb0bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324404"
---
# <a name="pass2-class"></a>Pass2 类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`Pass2`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[PASS2](../event-table.md#pass2)事件。

## <a name="syntax"></a>语法

```cpp
class Pass2 : public LinkerPass
{
public:
    Pass2(const RawEvent& event);
};
```

## <a name="members"></a>成员

除了从[LinkerPass](linker-pass.md)基类继承的成员一起，`Pass2`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[通行证2](#pass2)

## <a name="pass2"></a><a name="pass2"></a>通行证2

```cpp
Pass2(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[PASS2](../event-table.md#pass2)事件。

::: moniker-end
