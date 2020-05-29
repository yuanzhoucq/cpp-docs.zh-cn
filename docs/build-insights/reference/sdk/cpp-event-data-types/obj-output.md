---
title: Obj输出类
description: C++生成见解 SDK ObjOutput 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ObjOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 194253e8995401114e2529b868b36c9823510a4f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324497"
---
# <a name="objoutput-class"></a>Obj输出类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`ObjOutput`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[OBJ_OUTPUT](../event-table.md#obj-output)事件。

## <a name="syntax"></a>语法

```cpp
class ObjOutput : public FileOutput
{
public:
    ObjOutput(const RawEvent& event);
};
```

## <a name="members"></a>成员

除了从[FileOutput](file-output.md)基类继承的成员一起，`ObjOutput`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[Obj输出](#obj-output)

## <a name="objoutput"></a><a name="obj-output"></a>Obj输出

```cpp
ObjOutput(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[OBJ_OUTPUT](../event-table.md#obj-output)事件。

::: moniker-end
