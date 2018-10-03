---
title: 事件类 (WRL) |Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b28a6e9d30e7a31916582207901859045023ad66
ms.sourcegitcommit: d1527eb2d50156bf923f2a32ec3af9efc7fc4304
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48250951"
---
# <a name="event-class-wrl"></a>事件类 (WRL)

表示一个事件。

## <a name="syntax"></a>语法

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                   | 描述
---------------------- | ------------------------------------------------
[Event:: event](#event) | 初始化 `Event` 类的新实例。

### <a name="public-operators"></a>公共运算符

名称                                 | 描述
------------------------------------ | ------------------------------------------------------------------------
[Event:: operator =](#operator-assign) | 指定将分配`Event`对当前引用`Event`实例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HandleT`

`Event`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="event"></a>Event:: event

初始化 `Event` 类的新实例。

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>参数

*h*<br/>
事件的句柄。 默认情况下*h*初始化为`nullptr`。

## <a name="operator-assign"></a>Event:: operator =

指定将分配`Event`对当前引用`Event`实例。

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>参数

*h*<br/>
对的右值引用`Event`实例。

### <a name="return-value"></a>返回值

指向当前`Event`实例。
