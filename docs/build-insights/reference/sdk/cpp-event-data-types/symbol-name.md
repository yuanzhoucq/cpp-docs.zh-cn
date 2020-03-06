---
title: SymbolName 类
description: C++ BUILD Insights SDK SymbolName 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b5e9a9b22db99c099b9f7dc1813fb335358a83e8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334546"
---
# <a name="symbolname-class"></a>SymbolName 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`SymbolName` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[SYMBOL_NAME](../event-table.md#symbol-name)事件。

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

## <a name="members"></a>Members

除了其[SimpleEvent](simple-event.md)基类的继承成员以外，`SymbolName` 类包含以下成员：

### <a name="constructors"></a>构造函数

[SymbolName](#symbol-name)

### <a name="functions"></a>函数

[密钥](#key)
[名称](#name)

## <a name="key"></a>按键

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>返回值

此符号表示的类型的数值标识符。 此标识符在编译器前端传递中是唯一的。

## <a name="name"></a> 名称

```cpp
const char* Name() const;
```

### <a name="return-value"></a>返回值

由符号表示的类型的名称，用 UTF-8 编码。

## <a name="symbol-name"></a>SymbolName

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[SYMBOL_NAME](../event-table.md#symbol-name)事件。

::: moniker-end
