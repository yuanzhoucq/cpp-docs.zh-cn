---
title: 文件输入类
description: C++生成见解 SDK 文件输入类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileInput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 642236d3e67465ed38508cb24c8cd698ae880065
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324794"
---
# <a name="fileinput-class"></a>文件输入类

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

该`FileInput`类与[匹配事件](../functions/match-event.md)、[匹配事件在成员函数](../functions/match-event-in-member-function.md)、[匹配事件堆栈](../functions/match-event-stack.md)和[匹配事件堆栈功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[FILE_INPUT](../event-table.md#file-input)事件。

## <a name="syntax"></a>语法

```cpp
class FileInput : public SimpleEvent
{
public:
    enum class Type
    {
        OTHER               = FILE_TYPE_CODE_OTHER,
        OBJ                 = FILE_TYPE_CODE_OBJ,
        EXECUTABLE_IMAGE    = FILE_TYPE_CODE_EXECUTABLE_IMAGE,
        LIB                 = FILE_TYPE_CODE_LIB,
        IMP_LIB             = FILE_TYPE_CODE_IMP_LIB,
        EXP                 = FILE_TYPE_CODE_EXP
    };

    FileInput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>成员

除了其[SimpleEvent](simple-event.md)基类中继承的成员外，`FileInput`该类还包含以下成员：

### <a name="constructors"></a>构造函数

[文件输入](#file-input)

### <a name="functions"></a>函数

[路径](#path)
[类型](#type)

## <a name="fileinput"></a><a name="file-input"></a>文件输入

```cpp
FileInput(const RawEvent& event);
```

### <a name="parameters"></a>参数

*事件*\
[FILE_INPUT](../event-table.md#file-input)事件。

## <a name="path"></a><a name="path"></a>路径

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>返回值

输入文件的绝对路径。

## <a name="type"></a><a name="type"></a> 类型

```cpp
Type Type() const;
```

### <a name="return-value"></a>返回值

描述输入文件类型的代码。

::: moniker-end
