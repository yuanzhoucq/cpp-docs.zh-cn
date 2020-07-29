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
ms.openlocfilehash: 661d3cb92b20fc929a9bae3cad7bb55740e5e096
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213003"
---
# <a name="handlet-class"></a>HandleT 类

表示对象的句柄。

## <a name="syntax"></a>语法

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>参数

*HandleTraits*<br/>
定义句柄的常见特征的[HandleTraits](handletraits-structure.md)结构的实例。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称     | 描述
-------- | -----------------------------
`Traits` | `HandleTraits` 的同义词。

### <a name="public-constructors"></a>公共构造函数

名称                                | 描述
----------------------------------- | --------------------------------------------------
[HandleT：： HandleT](#handlet)        | 初始化 `HandleT` 类的新实例。
[HandleT：： ~ HandleT](#tilde-handlet) | 取消初始化类的实例 `HandleT` 。

### <a name="public-methods"></a>公共方法

“属性”                         | 描述
---------------------------- | ----------------------------------------------------------------------
[HandleT：： Attach](#attach)   | 将指定的句柄与当前的对象相关联 `HandleT` 。
[HandleT：： Close](#close)     | 关闭当前的 `HandleT` 对象。
[HandleT：:D etach](#detach)   | 将当前 `HandleT` 对象与其基础句柄解除。
[HandleT：： Get](#get)         | 获取基础句柄的值。
[HandleT：： IsValid](#isvalid) | 指示当前对象是否 `HandleT` 表示一个句柄。

### <a name="protected-methods"></a>受保护的方法

名称                                     | 描述
---------------------------------------- | ------------------------------------
[HandleT：： InternalClose](#internalclose) | 关闭当前的 `HandleT` 对象。

### <a name="public-operators"></a>公共运算符

名称                                   | 描述
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT：： operator =](#operator-assign) | 将指定对象的值移动 `HandleT` 到当前 `HandleT` 对象。

### <a name="protected-data-members"></a>受保护的数据成员

名称                        | 描述
--------------------------- | ----------------------------------------------------------------
[HandleT：： handle_](#handle) | 包含由对象表示的句柄 `HandleT` 。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HandleT`

## <a name="requirements"></a>要求

**标头：** corewrappers。h

**命名空间：** Microsoft：： WRL：：包装

## <a name="handlethandlet"></a><a name="tilde-handlet"></a>HandleT：： ~ HandleT

取消初始化类的实例 `HandleT` 。

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a>HandleT：： Attach

将指定的句柄与当前的对象相关联 `HandleT` 。

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>参数

*h*<br/>
句柄。

## <a name="handletclose"></a><a name="close"></a>HandleT：： Close

关闭当前的 `HandleT` 对象。

```cpp
void Close();
```

### <a name="remarks"></a>备注

当前的下层句柄 `HandleT` 关闭，并将 `HandleT` 设置为无效状态。

如果句柄关闭不正确，则调用线程中将引发异常。

## <a name="handletdetach"></a><a name="detach"></a>HandleT：:D etach

将当前 `HandleT` 对象与其基础句柄解除。

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>返回值

基础句柄。

### <a name="remarks"></a>备注

此操作完成后，当前 `HandleT` 设置为无效状态。

## <a name="handletget"></a><a name="get"></a>HandleT：： Get

获取基础句柄的值。

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>返回值

句柄。

## <a name="handlethandle_"></a><a name="handle"></a>HandleT：： handle_

包含由对象表示的句柄 `HandleT` 。

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a>HandleT：： HandleT

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

*h*<br/>
句柄。

### <a name="remarks"></a>备注

第一个构造函数初始化 `HandleT` 对象，该对象不是对象的有效句柄。 第二个构造函数 `HandleT` 从参数*h*创建新的对象。

## <a name="handletinternalclose"></a><a name="internalclose"></a>HandleT：： InternalClose

关闭当前的 `HandleT` 对象。

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>返回值

**`true`** 如果当前已 `HandleT` 成功关闭，则为; 否则为 **`false`** 。

### <a name="remarks"></a>备注

`InternalClose()`为 **`protected`** 。

## <a name="handletisvalid"></a><a name="isvalid"></a>HandleT：： IsValid

指示当前对象是否 `HandleT` 表示一个句柄。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果 `HandleT` 表示一个句柄，则为; 否则为 **`false`** 。

## <a name="handletoperator"></a><a name="operator-assign"></a>HandleT：： operator =

将指定对象的值移动 `HandleT` 到当前 `HandleT` 对象。

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>参数

*h*<br/>
对句柄的右值引用。

### <a name="return-value"></a>返回值

对当前对象的引用 `HandleT` 。

### <a name="remarks"></a>备注

此操作使 `HandleT` 参数*h*指定的对象失效。
