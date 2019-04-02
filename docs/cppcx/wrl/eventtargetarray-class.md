---
title: EventTargetArray 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
ms.openlocfilehash: 1f3f8e299dba1f4b6ae5a5767f11989dc2fe8370
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58783990"
---
# <a name="eventtargetarray-class"></a>EventTargetArray 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>备注

表示事件处理程序的数组。

与之关联的事件处理程序[EventSource](eventsource-class.md)对象存储在受保护`EventTargetArray`数据成员。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                           | 描述
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray::EventTargetArray](#eventtargetarray)        | 初始化 `EventTargetArray` 类的新实例。
[EventTargetArray::~EventTargetArray](#tilde-eventtargetarray) | 取消初始化当前`EventTargetArray`类。

### <a name="public-methods"></a>公共方法

名称                                  | 描述
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray::AddTail](#addtail) | 将指定的事件处理程序附加到事件处理程序的内部数组的末尾。
[EventTargetArray::Begin](#begin)     | 获取事件处理程序的内部数组中的第一个元素的地址。
[EventTargetArray::End](#end)         | 获取事件处理程序的内部数组中的最后一个元素的地址。
[EventTargetArray::Length](#length)   | 获取事件处理程序的内部数组中元素的当前数目。

## <a name="inheritance-hierarchy"></a>继承层次结构

`EventTargetArray`

## <a name="requirements"></a>要求

**标头：** event.h

**命名空间：** Microsoft::WRL::Details

## <a name="tilde-eventtargetarray"></a>EventTargetArray::~EventTargetArray

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>备注

取消初始化当前`EventTargetArray`类。

## <a name="addtail"></a>EventTargetArray::AddTail

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>参数

*element*<br/>
指向要追加的事件处理程序。

### <a name="remarks"></a>备注

将指定的事件处理程序附加到事件处理程序的内部数组的末尾。

`AddTail()` 应仅在内部使用`EventSource`类。

## <a name="begin"></a>EventTargetArray::Begin

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>返回值

事件处理程序在内部数组的第一个元素的地址。

### <a name="remarks"></a>备注

获取事件处理程序的内部数组中的第一个元素的地址。

## <a name="end"></a>EventTargetArray::End

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>返回值

事件处理程序在内部数组的最后一个元素的地址。

### <a name="remarks"></a>备注

获取事件处理程序的内部数组中的最后一个元素的地址。

## <a name="eventtargetarray"></a>EventTargetArray::EventTargetArray

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>参数

*hr*<br/>
此构造函数的操作之后, 参数*hr*指示数组的分配是成功还是失败。 以下列表显示的可能值*hr*。

+   S_OK<br/>
    操作成功。

+   E_OUTOFMEMORY<br/>
    无法为数组分配内存。

+   S_FALSE<br/>
    参数*项*小于或等于零。

*items*<br/>
要分配的数组元素数。

### <a name="remarks"></a>备注

初始化 `EventTargetArray` 类的新实例。

`EventTargetArray` 用于将数组中的事件处理程序`EventSource`对象。

## <a name="length"></a>EventTargetArray::Length

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
size_t Length();
```

### <a name="return-value"></a>返回值

当前的事件处理程序内部数组中的元素数。

### <a name="remarks"></a>备注

获取事件处理程序的内部数组中元素的当前数目。
