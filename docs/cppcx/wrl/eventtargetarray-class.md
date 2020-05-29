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
ms.openlocfilehash: 9ea8800aa22a6b5cae0b3342cf337786fb53fc76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371499"
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

与[EventSource](eventsource-class.md)对象关联的事件处理程序存储在受保护的`EventTargetArray`数据成员中。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                           | 说明
-------------------------------------------------------------- | -----------------------------------------------------------
[事件目标数组：事件目标数组](#eventtargetarray)        | 初始化 `EventTargetArray` 类的新实例。
[事件目标数组：*事件目标数组](#tilde-eventtargetarray) | 取消初始化当前`EventTargetArray`类。

### <a name="public-methods"></a>公共方法

名称                                  | 说明
------------------------------------- | ---------------------------------------------------------------------------------------
[事件目标数组：：添加尾翼](#addtail) | 将指定的事件处理程序追加到事件处理程序的内部数组的末尾。
[事件目标数组：：开始](#begin)     | 获取事件处理程序内部数组中第一个元素的地址。
[事件目标数组：结束](#end)         | 获取事件处理程序内部数组中最后一个元素的地址。
[事件目标数组：长度](#length)   | 获取事件处理程序内部数组中的当前元素数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`EventTargetArray`

## <a name="requirements"></a>要求

**标题：** 事件.h

**命名空间：** 微软：：WRL：:D

## <a name="eventtargetarrayeventtargetarray"></a><a name="tilde-eventtargetarray"></a>事件目标数组：*事件目标数组

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>备注

取消初始化当前`EventTargetArray`类。

## <a name="eventtargetarrayaddtail"></a><a name="addtail"></a>事件目标数组：：添加尾翼

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>参数

*元素*<br/>
指向要追加的事件处理程序的指针。

### <a name="remarks"></a>备注

将指定的事件处理程序追加到事件处理程序的内部数组的末尾。

`AddTail()`打算仅由`EventSource`类在内部使用。

## <a name="eventtargetarraybegin"></a><a name="begin"></a>事件目标数组：：开始

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>返回值

事件处理程序内部数组中第一个元素的地址。

### <a name="remarks"></a>备注

获取事件处理程序内部数组中第一个元素的地址。

## <a name="eventtargetarrayend"></a><a name="end"></a>事件目标数组：结束

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>返回值

事件处理程序内部数组中最后一个元素的地址。

### <a name="remarks"></a>备注

获取事件处理程序内部数组中最后一个元素的地址。

## <a name="eventtargetarrayeventtargetarray"></a><a name="eventtargetarray"></a>事件目标数组：事件目标数组

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>参数

*人力资源*<br/>
在此构造函数操作后，参数*hr*指示数组的分配是成功还是失败。 下面的列表显示了*hr*的可能值。

- S_OK<br/>
  操作成功。

- E_OUTOFMEMORY<br/>
  无法为阵列分配内存。

- S_FALSE<br/>
  参数*项*小于或等于零。

*项目*<br/>
要分配的数组元素的数量。

### <a name="remarks"></a>备注

初始化 `EventTargetArray` 类的新实例。

`EventTargetArray`用于在`EventSource`对象中保留事件处理程序数组。

## <a name="eventtargetarraylength"></a><a name="length"></a>事件目标数组：长度

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
size_t Length();
```

### <a name="return-value"></a>返回值

事件处理程序的内部数组中的当前元素数。

### <a name="remarks"></a>备注

获取事件处理程序内部数组中的当前元素数。
