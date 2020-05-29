---
title: 符号名称类
description: C++生成见解 SDK 符号名称类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1306fb43d6c2140a75b36c5f142532916cf26ae4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324357"
---
# <a name="symbolname-class"></a>符号名称类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`SymbolName`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[SYMBOL_NAME](../event-table.md#symbol-name)事件。

## <a name="syntax"></a>语法

```cpp
class SymbolName : public SimpleEvent
{
public:
    SymbolName(const RawEvent& event);

    const unsigned long long&  Key() const;
    const char*                Name() const;
};
```

## <a name="members"></a>成员

除了其[SimpleEvent](simple-event.md)基类中继承的成员外，`SymbolName`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[符号名称](#symbol-name)

### <a name="functions"></a>函数

[密钥](#key)
[名称](#name)

## <a name="key"></a><a name="key"></a>关键

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>返回值

此符号表示的类型的数字标识符。 此标识符在编译器前端传递中是唯一的。

## <a name="name"></a><a name="name"></a>名字

```cpp
const char* Name() const;
```

### <a name="return-value"></a>返回值

符号表示的类型的名称，以 UTF-8 编码。

## <a name="symbolname"></a><a name="symbol-name"></a>符号名称

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[SYMBOL_NAME](../event-table.md#symbol-name)事件。

::: moniker-end
