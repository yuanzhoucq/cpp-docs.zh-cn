---
title: 雷洛格瓦
description: C++生成见解 SDK RelogW 函数引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c5d5f6e35c7cd24d2324ce1d8a0434d9048b1d85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323809"
---
# <a name="relogw"></a>雷洛格瓦

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`RelogW`函数用于从 Windows （ETW） 跟踪的输入事件跟踪读取 MSVC 事件，并将它们写入新的修改后的 ETW 跟踪中。

## <a name="syntax"></a>语法

```cpp
enum RESULT_CODE RelogW(
    const wchar_t*          inputLogFile,
    const wchar_t*          outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>参数

*输入日志文件*\
要从中读取事件的输入 ETW 跟踪。

*输出日志文件*\
写入新事件的文件。

*重记录符*\
指向[RELOG_DESCRIPTOR](../other-types/relog-descriptor-struct.md)对象的指针。 使用此对象配置重新记录会话。

### <a name="return-value"></a>返回值

来自[RESULT_CODE](../other-types/result-code-enum.md)枚举的结果代码。

::: moniker-end
