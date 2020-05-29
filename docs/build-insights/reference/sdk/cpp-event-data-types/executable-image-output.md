---
title: 可执行图像输出类
description: C++生成见解 SDK 可执行图像输出类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ExecutableImageOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 834689a3605b729260f2d4c925396ee1af1bb705
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324946"
---
# <a name="executableimageoutput-class"></a>可执行图像输出类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`ExecutableImageOutput`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)事件。

## <a name="syntax"></a>语法

```cpp
class ExecutableImageOutput : public FileOutput
{
public:
    ExecutableImageOutput(const RawEvent& event);
};
```

## <a name="members"></a>成员

除了从[FileOutput](file-output.md)基类继承的成员一起，`ExecutableImageOutput`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[可执行图像输出](#executable-image-output)

## <a name="executableimageoutput"></a><a name="executable-image-output"></a>可执行图像输出

```cpp
ExecutableImageOutput(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)事件。

::: moniker-end
