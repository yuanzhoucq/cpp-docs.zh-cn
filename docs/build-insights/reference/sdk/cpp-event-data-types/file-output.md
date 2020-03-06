---
title: FileOutput 类
description: C++ BUILD Insights SDK FileOutput 类引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1c4053d0378ddb9d5dd061bbc9889c454dc9b52c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334840"
---
# <a name="fileoutput-class"></a>FileOutput 类

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

`FileOutput` 类用于[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函数。 用于匹配[EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)、 [EXP_OUTPUT](../event-table.md#exp-output)、 [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output)、 [LIB_OUTPUT](../event-table.md#lib-output)或[OBJ_OUTPUT](../event-table.md#obj-output)事件。

## <a name="syntax"></a>语法

```cpp
class FileOutput : public SimpleEvent
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

    FileOutput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>Members

除了其[SimpleEvent](simple-event.md)基类的继承成员以外，`FileOutput` 类包含以下成员：

### <a name="constructors"></a>构造函数

[FileOutput](#file-output)

### <a name="functions"></a>函数

[路径](#path)
[类型](#type)

## <a name="file-output"></a>FileOutput

```cpp
FileOutput(const RawEvent& event);
```

### <a name="parameters"></a>参数

*event*\
[EXECUTABLE_IMAGE_OUTPUT](../event-table.md#executable-image-output)、 [EXP_OUTPUT](../event-table.md#exp-output)、 [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output)、 [LIB_OUTPUT](../event-table.md#lib-output)或[OBJ_OUTPUT](../event-table.md#obj-output)事件。

## <a name="path"></a> Path

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>返回值

输出文件的绝对路径。

## <a name="type"></a>类别

```cpp
Type Type() const;
```

### <a name="return-value"></a>返回值

描述输出文件类型的代码。

::: moniker-end
