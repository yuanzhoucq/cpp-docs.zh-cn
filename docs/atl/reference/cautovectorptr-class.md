---
title: CAutoVectorPtr 类
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
ms.openlocfilehash: 8485f13b91c72d12c2084d2714f2acfa6dda7f01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478750"
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr 类

此类表示智能指针对象在使用矢量 new 和 delete 运算符。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<typename T>
class CAutoVectorPtr
```

#### <a name="parameters"></a>参数

*T*<br/>
指针类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|构造函数。|
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAutoVectorPtr::Allocate](#allocate)|调用此方法来分配对指向的对象的数组所需的内存`CAutoVectorPtr`。|
|[CAutoVectorPtr::Attach](#attach)|调用此方法以获取现有指针的所有权。|
|[CAutoVectorPtr::Detach](#detach)|调用此方法释放的指针的所有权。|
|[CAutoVectorPtr::Free](#free)|调用此方法以删除指向的对象`CAutoVectorPtr`。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAutoVectorPtr::operator T *](#operator_t__star)|强制转换运算符。|
|[CAutoVectorPtr::operator =](#operator_eq)|赋值运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAutoVectorPtr::m_p](#m_p)|指针数据成员变量。|

## <a name="remarks"></a>备注

此类提供用于创建和管理可帮助保护用户免受内存泄漏，它不再处于作用域时，会自动释放资源的智能指针的方法。 `CAutoVectorPtr` 类似于`CAutoPtr`，唯一的区别在于`CAutoVectorPtr`使用[向量新&#91;&#93; ](../../standard-library/new-operators.md#op_new_arr)并[向量删除&#91;&#93; ](../../standard-library/new-operators.md#op_delete_arr)来分配和释放内存而不是 c + +**新**并**删除**运算符。 请参阅[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)如果的集合类`CAutoVectorPtr`所需。

请参阅[CAutoPtr](../../atl/reference/cautoptr-class.md)有关使用智能指针类的示例。

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="allocate"></a>  CAutoVectorPtr::Allocate

调用此方法来分配对指向的对象的数组所需的内存`CAutoVectorPtr`。

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>参数

*nElements*<br/>
数组中的元素数。

### <a name="return-value"></a>返回值

分配的内存为成功时返回 true，false 失败。

### <a name="remarks"></a>备注

在调试版本中，如果出现断言失败[CAutoVectorPtr::m_p](#m_p)成员变量目前指向的现有值; 即，不等于 NULL。

##  <a name="attach"></a>  CAutoVectorPtr::Attach

调用此方法以获取现有指针的所有权。

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
`CAutoVectorPtr`对象将获得 this 指针的所有权。

### <a name="remarks"></a>备注

当`CAutoVectorPtr`对象采用的指针的所有权，它将自动删除指针和任何已分配的数据超出范围时。 如果[CAutoVectorPtr::Detach](#detach)是调用，程序员再次负责释放任何给定分配资源。

在调试版本中，如果出现断言失败[CAutoVectorPtr::m_p](#m_p)成员变量目前指向的现有值; 即，不等于 NULL。

##  <a name="cautovectorptr"></a>  CAutoVectorPtr::CAutoVectorPtr

构造函数。

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
现有的指针。

### <a name="remarks"></a>备注

`CAutoVectorPtr`可以使用现有指针创建对象，这种情况下它会将传输的指针的所有权。

##  <a name="dtor"></a>  CAutoVectorPtr:: ~ CAutoVectorPtr

析构函数。

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>备注

释放任何已分配的资源。 调用[CAutoVectorPtr::Free](#free)。

##  <a name="detach"></a>  CAutoVectorPtr::Detach

调用此方法释放的指针的所有权。

```
T* Detach() throw();
```

### <a name="return-value"></a>返回值

返回指针的副本。

### <a name="remarks"></a>备注

释放的指针的所有权，设置[CAutoVectorPtr::m_p](#m_p)成员变量为 NULL，并返回指针的副本。 在调用`Detach`，它由编程人员，以释放任何分配的资源对其`CAutoVectorPtr`对象可能已以前承担的责任。

##  <a name="free"></a>  CAutoVectorPtr::Free

调用此方法以删除指向的对象`CAutoVectorPtr`。

```
void Free() throw();
```

### <a name="remarks"></a>备注

指向的对象`CAutoVectorPtr`释放，并[CAutoVectorPtr::m_p](#m_p)成员变量设置为 NULL。

##  <a name="m_p"></a>  CAutoVectorPtr::m_p

指针数据成员变量。

```
T* m_p;
```

### <a name="remarks"></a>备注

此成员变量保存指针信息。

##  <a name="operator_eq"></a>  CAutoVectorPtr::operator =

赋值运算符。

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
一个指针。

### <a name="return-value"></a>返回值

返回的引用**CAutoVectorPtr\< T >**。

### <a name="remarks"></a>备注

赋值运算符分离`CAutoVectorPtr`从任何当前指针的对象，并将附加的新指针*p*，在其原位置。

##  <a name="operator_t__star"></a>  CAutoVectorPtr::operator T *

强制转换运算符。

```
operator T*() const throw();
```

### <a name="remarks"></a>备注

返回一个指向类模板中定义的对象数据类型。

## <a name="see-also"></a>请参阅

[CAutoPtr 类](../../atl/reference/cautoptr-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
