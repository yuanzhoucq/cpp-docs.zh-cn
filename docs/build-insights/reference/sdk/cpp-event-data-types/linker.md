---
title: 链接器类
description: C++生成见解 SDK 链接器类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Linker
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e5d4c0c3841377fc2e029c23d5cbbd076c8029cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324600"
---
# <a name="linker-class"></a>链接器类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`Linker`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[LINKER](../event-table.md#linker)事件。

## <a name="syntax"></a>语法

```cpp
class Linker : public Invocation
{
public:
    Linker(const RawEvent& event);
};
```

## <a name="members"></a>成员

除了从其[调用](invocation.md)基类继承的成员一起，`Linker`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[链接器](#linker)

## <a name="linker"></a><a name="linker"></a>连接

```cpp
Linker(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[链接器](../event-table.md#linker)事件。

::: moniker-end
