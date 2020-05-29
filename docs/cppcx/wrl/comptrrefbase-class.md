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
ms.openlocfilehash: 4f6dd6449cf8135ad14486d64cea95d8329e0014
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372619"
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
[ComPtr\<T>](comptr-class.md)类型或从它派生的类型，而不仅仅是 由 表示的`ComPtr`接口。

## <a name="remarks"></a>备注

表示[ComPtrRef](comptrref-class.md)类的基类。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称            | 说明
--------------- | -------------------------------------------------
`InterfaceType` | 模板参数*T*类型的同义词。

### <a name="public-operators"></a>公共运算符

名称                                                                       | 说明
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase：：操作员可检测*](#operator-iinspectable-star-star) | 将当前[ptr_](#ptr)数据成员转换为指向`IInspectable`接口的指针。
[ComPtrRefBase：：操作员I未知*](#operator-iunknown-star-star)         | 将当前[ptr_](#ptr)数据成员转换为指向`IUnknown`接口的指针。

### <a name="protected-data-members"></a>受保护的数据成员

名称                        | 说明
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase：:ptr]](#ptr) | 指向当前模板参数指定的类型。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ComPtrRefBase`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** 微软：：WRL：:D

## <a name="comptrrefbaseoperator-iinspectable-operator"></a><a name="operator-iinspectable-star-star"></a>ComPtrRefBase：：操作员可检查\*\*操作员

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>备注

将当前[ptr_](#ptr)数据成员转换为指向`IInspectable`接口的指针。

如果电流`ComPtrRefBase`未派生自`IInspectable`，则将发出错误。

此强制转换仅在定义时`__WRL_CLASSIC_COM__`才可用。

## <a name="comptrrefbaseoperator-iunknown-operator"></a><a name="operator-iunknown-star-star"></a>ComPtrRefBase：：操作员 I 未知* 运算符

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>备注

将当前[ptr_](#ptr)数据成员转换为指向`IUnknown`接口的指针。

如果电流`ComPtrRefBase`未派生自`IUnknown`，则将发出错误。

## <a name="comptrrefbaseptr_"></a><a name="ptr"></a>ComPtrRefBase：:ptr]

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
T* ptr_;
```

### <a name="remarks"></a>备注

指向当前模板参数指定的类型。 `ptr_`是受保护的数据成员。
