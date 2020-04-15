---
title: 事件类 （WRL）
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
ms.openlocfilehash: 85b4c2d1f1a27e90a65e47aa749e079f4aa08739
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371524"
---
# <a name="event-class-wrl"></a>事件类 （WRL）

表示一个事件。

## <a name="syntax"></a>语法

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                   | 说明
---------------------- | ------------------------------------------------
[事件：事件](#event) | 初始化 `Event` 类的新实例。

### <a name="public-operators"></a>公共运算符

名称                                 | 说明
------------------------------------ | ------------------------------------------------------------------------
[事件：：操作员*](#operator-assign) | 将指定的`Event`引用分配给当前`Event`实例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HandleT`

`Event`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装

## <a name="eventevent"></a><a name="event"></a>事件：事件

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

*H*<br/>
事件的句柄。 默认情况下 *，h*初始化到`nullptr`。

## <a name="eventoperator"></a><a name="operator-assign"></a>事件：：操作员*

将指定的`Event`引用分配给当前`Event`实例。

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>参数

*H*<br/>
实例的`Event`rvalue 引用。

### <a name="return-value"></a>返回值

指向当前`Event`实例的指针。
