---
title: 前端文件类
description: C++生成见解 SDK 前端文件类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c40137724279ea2fd615729db39f0ac5c907b79e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324763"
---
# <a name="frontendfile-class"></a>前端文件类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`FrontEndFile`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[FRONT_END_FILE](../event-table.md#front-end-file)事件。

## <a name="syntax"></a>语法

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>成员

除了从[其活动](activity.md)基类继承的成员外，`FrontEndFile`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[前端文件](#front-end-file)

### <a name="functions"></a>函数

[路径](#path)

## <a name="frontendfile"></a><a name="front-end-file"></a>前端文件

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[FRONT_END_FILE](../event-table.md#front-end-file)事件。

## <a name="path"></a><a name="path"></a>路径

```cpp
const char* Path() const;
```

### <a name="return-value"></a>返回值

文件的绝对路径，以 UTF-8 编码。

::: moniker-end
