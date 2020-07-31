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
ms.openlocfilehash: 65d37396b02d2c11c758915b201eef09cf1935b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226641"
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr 类

此类表示使用向量 new 和 delete 运算符的智能指针对象。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

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

|名称|说明|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|构造函数。|
|[CAutoVectorPtr：： ~ CAutoVectorPtr](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CAutoVectorPtr：： Allocate](#allocate)|调用此方法以分配由所指向的对象数组所需的内存 `CAutoVectorPtr` 。|
|[CAutoVectorPtr：： Attach](#attach)|调用此方法以获取现有指针的所有权。|
|[CAutoVectorPtr：:D etach](#detach)|调用此方法可释放指针的所有权。|
|[CAutoVectorPtr：： Free](#free)|调用此方法以删除指向的对象 `CAutoVectorPtr` 。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAutoVectorPtr：： operator T *](#operator_t__star)|转换运算符。|
|[CAutoVectorPtr：： operator =](#operator_eq)|赋值运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CAutoVectorPtr：： m_p](#m_p)|指针数据成员变量。|

## <a name="remarks"></a>备注

此类提供用于创建和管理智能指针的方法，通过在资源超出范围时自动释放资源，帮助防止内存泄漏。 `CAutoVectorPtr`与类似 `CAutoPtr` ，唯一的差别在于， `CAutoVectorPtr` 使用[向量 new&#91;&#93;](../../standard-library/new-operators.md#op_new_arr)和[矢量 delete&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr)来分配和释放内存，而不是使用 c + + **`new`** 和 **`delete`** 运算符。 如果需要的集合类，请参阅[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) `CAutoVectorPtr` 。

有关使用智能指针类的示例，请参阅[CAutoPtr](../../atl/reference/cautoptr-class.md) 。

## <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr：： Allocate

调用此方法以分配由所指向的对象数组所需的内存 `CAutoVectorPtr` 。

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>参数

*nElements*<br/>
数组中的元素数。

### <a name="return-value"></a>返回值

如果内存分配成功，则返回 true，否则返回 false。

### <a name="remarks"></a>备注

在调试版本中，如果[CAutoVectorPtr：： m_p](#m_p)成员变量当前指向现有值，则将发生断言失败;也就是说，它不等于 NULL。

## <a name="cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr：： Attach

调用此方法以获取现有指针的所有权。

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>参数

*h-p*<br/>
`CAutoVectorPtr`对象将取得此指针的所有权。

### <a name="remarks"></a>备注

当 `CAutoVectorPtr` 对象取得指针的所有权时，它会在超出范围时自动删除指针和任何分配的数据。 如果调用[CAutoVectorPtr：:D etach](#detach) ，则将再次为程序员提供释放任何已分配资源的责任。

在调试版本中，如果[CAutoVectorPtr：： m_p](#m_p)成员变量当前指向现有值，则将发生断言失败;也就是说，它不等于 NULL。

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr

构造函数。

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>参数

*h-p*<br/>
现有指针。

### <a name="remarks"></a>备注

`CAutoVectorPtr`对象可使用现有指针创建，在这种情况下，它会传输指针的所有权。

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr：： ~ CAutoVectorPtr

析构函数。

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。 调用[CAutoVectorPtr：： Free](#free)。

## <a name="cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr：:D etach

调用此方法可释放指针的所有权。

```
T* Detach() throw();
```

### <a name="return-value"></a>返回值

返回指针的副本。

### <a name="remarks"></a>备注

释放指针的所有权，将[CAutoVectorPtr：： m_p](#m_p)成员变量设置为 NULL，并返回指针的副本。 调用后 `Detach` ，程序员需要释放任何已分配的资源，该对象在此 `CAutoVectorPtr` 之前可能会承担该对象。

## <a name="cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr：： Free

调用此方法以删除指向的对象 `CAutoVectorPtr` 。

```cpp
void Free() throw();
```

### <a name="remarks"></a>备注

将释放由指向的对象 `CAutoVectorPtr` ，并将[CAutoVectorPtr：： m_p](#m_p)成员变量设置为 NULL。

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>CAutoVectorPtr：： m_p

指针数据成员变量。

```
T* m_p;
```

### <a name="remarks"></a>备注

此成员变量保存指针信息。

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr：： operator =

赋值运算符。

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>参数

*h-p*<br/>
一个指针。

### <a name="return-value"></a>返回值

返回对**CAutoVectorPtr \< T > **的引用。

### <a name="remarks"></a>备注

赋值运算符将 `CAutoVectorPtr` 对象与任何当前指针分离，并将新的指针*p*附加到其位置。

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr：： operator T *

转换运算符。

```
operator T*() const throw();
```

### <a name="remarks"></a>备注

返回一个指针，该指针指向在类模板中定义的对象数据类型。

## <a name="see-also"></a>另请参阅

[CAutoPtr 类](../../atl/reference/cautoptr-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
