---
title: FileInput 类
description: C++ BUILD Insights SDK FileInput 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileInput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bea2cf72ca2a83a9cd630f8a9ccefb87dd4b7ff1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334846"
---
# <a name="fileinput-class"></a>FileInput 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`FileInput` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 使用它来匹配[FILE_INPUT](../event-table.md#file-input)事件。

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

## <a name="members"></a>Members

除了其[SimpleEvent](simple-event.md)基类的继承成员以外，`FileInput` 类包含以下成员：

### <a name="constructors"></a>构造函数

[FileInput](#file-input)

### <a name="functions"></a>函数

[路径](#path)
[类型](#type)

## <a name="file-input"></a>FileInput

```cpp
FileInput(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[FILE_INPUT](../event-table.md#file-input)事件。

## <a name="path"></a> Path

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>返回值

输入文件的绝对路径。

## <a name="type"></a>类别

```cpp
Type Type() const;
```

### <a name="return-value"></a>返回值

描述输入文件类型的代码。

::: moniker-end
