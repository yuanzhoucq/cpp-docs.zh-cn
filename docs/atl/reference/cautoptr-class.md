---
title: CAutoPtr 类
ms.date: 11/04/2016
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
ms.openlocfilehash: cb8e3d6b71db6ab60b3b246bd8c5bf4f2c9aaa34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321260"
---
# <a name="cautoptr-class"></a>CAutoPtr 类

此类表示智能指针对象。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <typename T>
class CAutoPtr
```

#### <a name="parameters"></a>参数

*T*<br/>
指针类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAutoPtr：CAutoPtr](#cautoptr)|构造函数。|
|[CAutoPtr：_CAutoPtr](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAutoPtr：：附加](#attach)|调用此方法以获取现有指针的所有权。|
|[CAutoPtr：:D塔奇](#detach)|调用此方法以释放指针的所有权。|
|[CAutoPtr：免费](#free)|调用此方法以删除 指向 的对象`CAutoPtr`。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAutoPtr：：操作员T*](#operator_t_star)|强制转换运算符。|
|[CAutoPtr：：运算符 |](#operator_eq)|分配运算符。|
|[CAutoPtr：运算符 ->](#operator_ptr)|指针到成员运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CAutoPtr：m_p](#m_p)|指针数据成员变量。|

## <a name="remarks"></a>备注

此类提供创建和管理智能指针的方法，通过在资源出镜范围时自动释放资源，这将有助于防止内存泄漏。

此外，`CAutoPtr`复制构造函数和赋值运算符转移指针的所有权，将源指针复制到目标指针并将源指针设置为 NULL。 因此，不可能有两`CAutoPtr`个对象每个存储相同的指针，这减少了删除同一指针两次的可能性。

`CAutoPtr`还简化了指针集合的创建。 与其派生集合类并重写析构函数，不如创建`CAutoPtr`对象集合。 删除集合时，`CAutoPtr`对象将超出范围并自动删除自身。

[CHeapPtr](../../atl/reference/cheapptr-class.md)和变体的工作方式与`CAutoPtr`相同，只是它们使用不同的堆函数（而不是**C++新的**运算符和**删除**运算符分配和释放内存。 [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)与`CAutoPtr`类似，唯一的区别是它使用**矢量 new_** 和**矢量删除*** 来分配和释放内存。

当需要数组或智能指针列表时，请参阅[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)和[CAutoPtrList。](../../atl/reference/cautoptrlist-class.md)

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr：：附加

调用此方法以获取现有指针的所有权。

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
该`CAutoPtr`对象将取得此指针的所有权。

### <a name="remarks"></a>备注

当对象`CAutoPtr`取得指针的所有权时，当它超出范围时，它将自动删除指针和任何已分配的数据。 如果调用[CAutoPtr：:Detach，](#detach)程序员将再次被赋予释放任何分配资源的责任。

在调试生成中，如果[CAutoPtr：：m_p](#m_p)数据成员当前指向现有值，则断言失败将发生;也就是说，它不等于 NULL。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr：CAutoPtr

构造函数。

```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
现有指针。

*TSrc*<br/>
由另一个`CAutoPtr`管理的类型，用于初始化当前对象。

### <a name="remarks"></a>备注

可以使用`CAutoPtr`现有指针创建对象，在这种情况下，该对象会转移指针的所有权。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr：_CAutoPtr

析构函数。

```
~CAutoPtr() throw();
```

### <a name="remarks"></a>备注

释放任何分配的资源。 呼叫[CAutoPtr：：免费](#free)。

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr：:D塔奇

调用此方法以释放指针的所有权。

```
T* Detach() throw();
```

### <a name="return-value"></a>返回值

返回指针的副本。

### <a name="remarks"></a>备注

释放指针的所有权，将[CAutoPtr：：m_p](#m_p)数据成员变量设置为 NULL，并返回指针的副本。 调用`Detach`后，由程序员释放`CAutoPtr`对象以前可能假定可重现的任何分配资源。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr：免费

调用此方法以删除 指向 的对象`CAutoPtr`。

```
void Free() throw();
```

### <a name="remarks"></a>备注

释放 指向`CAutoPtr`的对象[，CAutoPtr：：m_p](#m_p)数据成员变量设置为 NULL。

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr：m_p

指针数据成员变量。

```
T* m_p;
```

### <a name="remarks"></a>备注

此成员变量保存指针信息。

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr：：运算符 |

分配运算符。

```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>参数

*P*<br/>
指针。

*TSrc*<br/>
类类型。

### <a name="return-value"></a>返回值

返回对**CAutoPtr\< T 的引用>**。

### <a name="remarks"></a>备注

赋值运算符从任何当前`CAutoPtr`指针分离对象，并将新指针*p*将其附加在其位置。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr：运算符 -&gt;

指针到成员运算符。

```
T* operator->() const throw();
```

### <a name="return-value"></a>返回值

返回[CAutoPtr：：m_p](#m_p)数据成员变量的值。

### <a name="remarks"></a>备注

使用此运算符调用`CAutoPtr`对象指向的类中的方法。 在调试生成中，如果指向 NULL，`CAutoPtr`则会发生断言失败。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr：：操作员T*

强制转换运算符。

```
operator T* () const throw();
```

### <a name="return-value"></a>返回值

返回指向类模板中定义的对象数据类型的指针。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="see-also"></a>另请参阅

[CHeapPtr 类](../../atl/reference/cheapptr-class.md)<br/>
[CAutoVectorPtr 类](../../atl/reference/cautovectorptr-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
