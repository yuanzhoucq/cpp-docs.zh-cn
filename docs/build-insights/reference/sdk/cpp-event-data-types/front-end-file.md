---
title: FrontEndFile 类
description: C++ BUILD Insights SDK FrontEndFile 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 094b1326765e0e8edb00534ecb3d94c46702d4ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334792"
---
# <a name="frontendfile-class"></a>FrontEndFile 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`FrontEndFile` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[FRONT_END_FILE](../event-table.md#front-end-file)事件。

## <a name="syntax"></a>语法

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>Members

除了其[活动](activity.md)基类的继承成员以外，`FrontEndFile` 类包含以下成员：

### <a name="constructors"></a>构造函数

[FrontEndFile](#front-end-file)

### <a name="functions"></a>函数

[Path](#path)

## <a name="front-end-file"></a>FrontEndFile

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[FRONT_END_FILE](../event-table.md#front-end-file)事件。

## <a name="path"></a> Path

```cpp
const char* Path() const;
```

### <a name="return-value"></a>返回值

文件的绝对路径，以 UTF-8 编码。

::: moniker-end
