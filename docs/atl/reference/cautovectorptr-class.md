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
ms.openlocfilehash: fc4bd4ba7a2f41a25679f1da718671f525519708
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748215"
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr 类

此类表示使用矢量新运算符和删除运算符的智能指针对象。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

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
|[C自动矢量器：C自动矢量器](#cautovectorptr)|构造函数。|
|[C自动矢量器：：*C自动矢量Ptr](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C自动矢量器：分配](#allocate)|调用此方法以分配 所`CAutoVectorPtr`指向的对象数组所需的内存。|
|[C自动矢量器：：附加](#attach)|调用此方法以获取现有指针的所有权。|
|[CAutoVectorPtr：:Detach](#detach)|调用此方法以释放指针的所有权。|
|[CAutoVectorPtr：免费](#free)|调用此方法以删除 指向 的对象`CAutoVectorPtr`。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAutoVectorPtr：运算符 T |](#operator_t__star)|强制转换运算符。|
|[CAutoVectorPtr：：运算符 |](#operator_eq)|分配运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C自动矢量器：：m_p](#m_p)|指针数据成员变量。|

## <a name="remarks"></a>备注

此类提供创建和管理智能指针的方法，通过在资源出镜范围时自动释放资源，这将有助于防止内存泄漏。 `CAutoVectorPtr`与 类似`CAutoPtr`，唯一的`CAutoVectorPtr`区别是使用[矢量新&#91;&#93;](../../standard-library/new-operators.md#op_new_arr)和[矢量删除&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr)分配和释放内存，而不是C++**新的**和**删除**运算符。 如果需要 的收集类，`CAutoVectorPtr`请参阅[CAutoVectorPtrElementTraits。](../../atl/reference/cautovectorptrelementtraits-class.md)

有关使用智能指针类的示例，请参阅[CAutoPtr。](../../atl/reference/cautoptr-class.md)

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>C自动矢量器：分配

调用此方法以分配 所`CAutoVectorPtr`指向的对象数组所需的内存。

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>参数

*n元素*<br/>
数组中的元素数。

### <a name="return-value"></a>返回值

如果内存成功分配，则返回 true，在失败时为 false。

### <a name="remarks"></a>备注

在调试生成中，如果[CAutoVectorPtr：：m_p](#m_p)成员变量当前指向现有值，则断言失败将发生;也就是说，它不等于 NULL。

## <a name="cautovectorptrattach"></a><a name="attach"></a>C自动矢量器：：附加

调用此方法以获取现有指针的所有权。

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
该`CAutoVectorPtr`对象将取得此指针的所有权。

### <a name="remarks"></a>备注

当对象`CAutoVectorPtr`取得指针的所有权时，当它超出范围时，它将自动删除指针和任何已分配的数据。 如果调用[CAutoVectorPtr：:Detach，](#detach)程序员将再次被赋予释放任何分配资源的责任。

在调试生成中，如果[CAutoVectorPtr：：m_p](#m_p)成员变量当前指向现有值，则断言失败将发生;也就是说，它不等于 NULL。

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>C自动矢量器：C自动矢量器

构造函数。

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
现有指针。

### <a name="remarks"></a>备注

可以使用`CAutoVectorPtr`现有指针创建对象，在这种情况下，该对象会转移指针的所有权。

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>C自动矢量器：：*C自动矢量Ptr

析构函数。

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>备注

释放任何分配的资源。 调用[CAutoVectorPtr：：免费](#free)。

## <a name="cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr：:Detach

调用此方法以释放指针的所有权。

```
T* Detach() throw();
```

### <a name="return-value"></a>返回值

返回指针的副本。

### <a name="remarks"></a>备注

释放指针的所有权，将[CAutoVectorPtr：：m_p](#m_p)成员变量设置为 NULL，并返回指针的副本。 调用`Detach`后，由程序员释放`CAutoVectorPtr`对象以前可能承担的任何分配的资源。

## <a name="cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr：免费

调用此方法以删除 指向 的对象`CAutoVectorPtr`。

```cpp
void Free() throw();
```

### <a name="remarks"></a>备注

释放 下`CAutoVectorPtr`指向的对象[，CAutoVectorPtr：：m_p](#m_p)成员变量设置为 NULL。

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>C自动矢量器：：m_p

指针数据成员变量。

```
T* m_p;
```

### <a name="remarks"></a>备注

此成员变量保存指针信息。

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr：：运算符 |

分配运算符。

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指针。

### <a name="return-value"></a>返回值

返回对**CAutoVectorPtr\< T 的引用>**。

### <a name="remarks"></a>备注

赋值运算符从任何当前`CAutoVectorPtr`指针分离对象，并将新指针*p*将其附加在其位置。

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr：运算符 T |

强制转换运算符。

```
operator T*() const throw();
```

### <a name="remarks"></a>备注

返回指向类模板中定义的对象数据类型的指针。

## <a name="see-also"></a>请参阅

[CAutoPtr 类](../../atl/reference/cautoptr-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
