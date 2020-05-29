---
title: 前端文件组类
description: C++生成见解 SDK 前端文件组类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d2eebb650e59e750e5ebde74914dca5f0ef4779d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324752"
---
# <a name="frontendfilegroup-class"></a>前端文件组类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`FrontEndFileGroup`类与[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackIn会员函数一](../functions/match-event-stack-in-member-function.md)起使用。 使用它匹配[FRONT_END_FILE](../event-table.md#front-end-file)事件组。

## <a name="syntax"></a>语法

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>成员

除了从[其 EventGroup\<FrontEndFile\>](event-group.md)基类继承的成员一起，该`FrontEndFileGroup`类还包含以下成员：

### <a name="constructors"></a>构造函数

[前端文件组](#front-end-file-group)

## <a name="frontendfilegroup"></a><a name="front-end-file-group"></a>前端文件组

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>参数

*组*\
一组[FRONT_END_FILE](../event-table.md#front-end-file)事件。

::: moniker-end
