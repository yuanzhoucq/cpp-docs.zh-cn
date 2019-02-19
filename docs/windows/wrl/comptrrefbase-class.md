---
title: ComPtrRefBase 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
- client/Microsoft::WRL::Details::ComPtrRefBase::ptr_
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRefBase class
- Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable** operator
- Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown** operator
- Microsoft::WRL::Details::ComPtrRefBase::ptr_ data member
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
ms.openlocfilehash: df4e2aa1ce650fd5b1f04baf2f7c4cd2fb4cff93
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335789"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>参数

*T*<br/>
一个[ComPtr\<T >](comptr-class.md)类型派生自它，而不仅仅是所表示接口`ComPtr`。

## <a name="remarks"></a>备注

表示类的基类[ComPtrRef](comptrref-class.md)类。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称            | 描述
--------------- | -------------------------------------------------
`InterfaceType` | 模板参数的类型的同义词*T*。

### <a name="public-operators"></a>公共运算符

名称                                                                       | 描述
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[Comptrrefbase:: Operator IInspectable * *](#operator-iinspectable-star-star) | 将当前[ptr_](#ptr)数据成员添加到指针-到-a-指针-到`IInspectable`接口。
[Comptrrefbase:: Operator IUnknown * *](#operator-iunknown-star-star)         | 将当前[ptr_](#ptr)数据成员添加到指针-到-a-指针-到`IUnknown`接口。

### <a name="protected-data-members"></a>受保护的数据成员

name                        | 描述
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::ptr_](#ptr) | 为当前的模板参数指定的类型的指针。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ComPtrRefBase`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL::Details

## <a name="operator-iinspectable-star-star"></a>Comptrrefbase:: Operator IInspectable\* \*运算符

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>备注

将当前[ptr_](#ptr)数据成员添加到指针-到-a-指针-到`IInspectable`接口。

如果发出错误当前`ComPtrRefBase`也不是派生`IInspectable`。

此强制转换为可用才`__WRL_CLASSIC_COM__`定义。

## <a name="operator-iunknown-star-star"></a>Comptrrefbase:: Operator IUnknown * * 运算符

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>备注

将当前[ptr_](#ptr)数据成员添加到指针-到-a-指针-到`IUnknown`接口。

如果发出错误当前`ComPtrRefBase`也不是派生`IUnknown`。

## <a name="ptr"></a>ComPtrRefBase::ptr_

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
T* ptr_;
```

### <a name="remarks"></a>备注

为当前的模板参数指定的类型的指针。 `ptr_` 是受保护的数据成员。
