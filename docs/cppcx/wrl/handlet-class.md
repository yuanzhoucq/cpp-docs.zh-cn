---
title: HandleT 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Get
- corewrappers/Microsoft::WRL::Wrappers::HandleT::handle_
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
- corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
- corewrappers/Microsoft::WRL::Wrappers::HandleT::~HandleT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleT class
- Microsoft::WRL::Wrappers::HandleT::Attach method
- Microsoft::WRL::Wrappers::HandleT::Close method
- Microsoft::WRL::Wrappers::HandleT::Detach method
- Microsoft::WRL::Wrappers::HandleT::Get method
- Microsoft::WRL::Wrappers::HandleT::handle_ data member
- Microsoft::WRL::Wrappers::HandleT::HandleT, constructor
- Microsoft::WRL::Wrappers::HandleT::InternalClose method
- Microsoft::WRL::Wrappers::HandleT::IsValid method
- Microsoft::WRL::Wrappers::HandleT::operator= operator
- Microsoft::WRL::Wrappers::HandleT::~HandleT, destructor
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
ms.openlocfilehash: bde7d7f1bd6730d96cb0f7a0d191a32eb8ed3e8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371456"
---
# <a name="handlet-class"></a>HandleT 类

表示对象的句柄。

## <a name="syntax"></a>语法

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>参数

*处理特征*<br/>
定义句柄的常见特征的[HandleTraits](handletraits-structure.md)结构的实例。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称     | 说明
-------- | -----------------------------
`Traits` | `HandleTraits` 的同义词。

### <a name="public-constructors"></a>公共构造函数

名称                                | 说明
----------------------------------- | --------------------------------------------------
[手柄T：：手柄T](#handlet)        | 初始化 `HandleT` 类的新实例。
[手柄T：=手柄T](#tilde-handlet) | 取消初始化类的`HandleT`实例。

### <a name="public-methods"></a>公共方法

名称                         | 说明
---------------------------- | ----------------------------------------------------------------------
[句柄T：：附加](#attach)   | 将指定的句柄与当前`HandleT`对象关联。
[手柄T：关闭](#close)     | 关闭当前的 `HandleT` 对象。
[手柄T：:D埃塔奇](#detach)   | 将当前`HandleT`对象与其基础句柄分离。
[句柄T：获取](#get)         | 获取基础句柄的值。
[句柄T：有效](#isvalid) | 指示当前`HandleT`对象是否表示句柄。

### <a name="protected-methods"></a>受保护的方法

名称                                     | 说明
---------------------------------------- | ------------------------------------
[句柄T：：内部关闭](#internalclose) | 关闭当前的 `HandleT` 对象。

### <a name="public-operators"></a>公共运算符

名称                                   | 说明
-------------------------------------- | ----------------------------------------------------------------------------------
[手柄：：运算符*](#operator-assign) | 将指定`HandleT`对象的值移动到当前`HandleT`对象。

### <a name="protected-data-members"></a>受保护的数据成员

名称                        | 说明
--------------------------- | ----------------------------------------------------------------
[手柄：：handle_](#handle) | 包含由对象表示的`HandleT`句柄。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HandleT`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装

## <a name="handlethandlet"></a><a name="tilde-handlet"></a>手柄T：=手柄T

取消初始化类的`HandleT`实例。

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a>句柄T：：附加

将指定的句柄与当前`HandleT`对象关联。

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>参数

*H*<br/>
句柄。

## <a name="handletclose"></a><a name="close"></a>手柄T：关闭

关闭当前的 `HandleT` 对象。

```cpp
void Close();
```

### <a name="remarks"></a>备注

当前的基础句柄`HandleT`已关闭，`HandleT`并且设置为无效状态。

如果句柄关闭不正确，则调用线程中将引发异常。

## <a name="handletdetach"></a><a name="detach"></a>手柄T：:D埃塔奇

将当前`HandleT`对象与其基础句柄分离。

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>返回值

基础句柄。

### <a name="remarks"></a>备注

此操作完成后，电流`HandleT`将设置为无效状态。

## <a name="handletget"></a><a name="get"></a>句柄T：获取

获取基础句柄的值。

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>返回值

句柄。

## <a name="handlethandle_"></a><a name="handle"></a>手柄：：handle_

包含由对象表示的`HandleT`句柄。

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a>手柄T：：手柄T

初始化 `HandleT` 类的新实例。

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>参数

*H*<br/>
句柄。

### <a name="remarks"></a>备注

第一个`HandleT`构造函数初始化不是对象的有效句柄的对象。 第二个构造函数从参数`HandleT` *h*创建一个新对象。

## <a name="handletinternalclose"></a><a name="internalclose"></a>句柄T：：内部关闭

关闭当前的 `HandleT` 对象。

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>返回值

**如果**当前`HandleT`成功关闭，为 true;否则，**假**。

### <a name="remarks"></a>备注

`InternalClose()` 为 `protected`。

## <a name="handletisvalid"></a><a name="isvalid"></a>句柄T：有效

指示当前`HandleT`对象是否表示句柄。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>返回值

如果 表示`HandleT`句柄，**则为 true;** 否则，**假**。

## <a name="handletoperator"></a><a name="operator-assign"></a>手柄：：运算符*

将指定`HandleT`对象的值移动到当前`HandleT`对象。

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>参数

*H*<br/>
对句柄的 rvalue 引用。

### <a name="return-value"></a>返回值

对当前`HandleT`对象的引用。

### <a name="remarks"></a>备注

此操作使参数*h*`HandleT`指定的对象无效。
