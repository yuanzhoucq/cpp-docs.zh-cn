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
ms.openlocfilehash: 699e62362bc74009e3faed3b4fd66b579c9c4cd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226654"
---
# <a name="cautoptr-class"></a>CAutoPtr 类

此类表示智能指针对象。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```cpp
template <typename T>
class CAutoPtr
```

### <a name="parameters"></a>参数

*T*<br/>
指针类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|构造函数。|
|[CAutoPtr：： ~ CAutoPtr](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CAutoPtr：： Attach](#attach)|调用此方法以获取现有指针的所有权。|
|[CAutoPtr：:D etach](#detach)|调用此方法可释放指针的所有权。|
|[CAutoPtr：： Free](#free)|调用此方法以删除指向的对象 `CAutoPtr` 。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAutoPtr：： operator T *](#operator_t_star)|转换运算符。|
|[CAutoPtr：： operator =](#operator_eq)|赋值运算符。|
|[CAutoPtr：： operator->](#operator_ptr)|指向成员的指针运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CAutoPtr：： m_p](#m_p)|指针数据成员变量。|

## <a name="remarks"></a>备注

此类提供用于创建和管理智能指针的方法，通过在资源超出范围时自动释放资源，帮助防止内存泄漏。

此外， `CAutoPtr` 的复制构造函数和赋值运算符会传输指针的所有权，将源指针复制到目标指针，并将源指针设置为 NULL。 因此， `CAutoPtr` 每个对象都不能存储同一个指针，这就减少了两次删除相同指针的可能性。

`CAutoPtr`还简化了指针集合的创建。 更简单的方法是创建一个对象集合，而不是派生集合类并重写析构函数 `CAutoPtr` 。 删除集合时， `CAutoPtr` 对象将超出范围并自动删除。

[CHeapPtr](../../atl/reference/cheapptr-class.md)和变体的工作方式与相同 `CAutoPtr` ，不同之处在于它们使用不同的堆函数（而不是 c + + 和运算符）分配和释放内存 **`new`** **`delete`** 。 [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)类似于 `CAutoPtr` ，唯一的区别在于，它使用**vector new []** 和**向量 delete []** 来分配和释放内存。

若需要智能指针的数组或列表，请参阅[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)和[CAutoPtrList](../../atl/reference/cautoptrlist-class.md) 。

## <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr：： Attach

调用此方法以获取现有指针的所有权。

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>参数

*h-p*<br/>
`CAutoPtr`对象将取得此指针的所有权。

### <a name="remarks"></a>备注

当 `CAutoPtr` 对象取得指针的所有权时，它会在超出范围时自动删除指针和任何分配的数据。 如果调用[CAutoPtr：:D etach](#detach) ，则将再次为程序员提供释放任何已分配资源的责任。

在调试版本中，如果[CAutoPtr：： m_p](#m_p)数据成员当前指向现有值，则将发生断言失败;也就是说，它不等于 NULL。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr::CAutoPtr

构造函数。

```cpp
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>参数

*h-p*<br/>
现有指针。

*TSrc*<br/>
由另一类型管理 `CAutoPtr` ，用于初始化当前对象。

### <a name="remarks"></a>备注

`CAutoPtr`对象可使用现有指针创建，在这种情况下，它会传输指针的所有权。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr：： ~ CAutoPtr

析构函数。

```cpp
~CAutoPtr() throw();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。 调用[CAutoPtr：： Free](#free)。

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr：:D etach

调用此方法可释放指针的所有权。

```cpp
T* Detach() throw();
```

### <a name="return-value"></a>返回值

返回指针的副本。

### <a name="remarks"></a>备注

释放指针的所有权，将[CAutoPtr：： m_p](#m_p)数据成员变量设置为 NULL，并返回指针的副本。 调用后 `Detach` ，程序员需要释放任何已分配的资源， `CAutoPtr` 对象先前可能会假设 reponsibility。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr：： Free

调用此方法以删除指向的对象 `CAutoPtr` 。

```cpp
void Free() throw();
```

### <a name="remarks"></a>备注

已释放由指向的对象 `CAutoPtr` ，并且[CAutoPtr：： m_p](#m_p)数据成员变量设置为 NULL。

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr：： m_p

指针数据成员变量。

```cpp
T* m_p;
```

### <a name="remarks"></a>备注

此成员变量保存指针信息。

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr：： operator =

赋值运算符。

```cpp
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>参数

*h-p*<br/>
一个指针。

*TSrc*<br/>
类类型。

### <a name="return-value"></a>返回值

返回对**CAutoPtr \< T > **的引用。

### <a name="remarks"></a>备注

赋值运算符将 `CAutoPtr` 对象与任何当前指针分离，并将新的指针*p*附加到其位置。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr：： operator-&gt;

指向成员的指针运算符。

```cpp
T* operator->() const throw();
```

### <a name="return-value"></a>返回值

返回[CAutoPtr：： m_p](#m_p)数据成员变量的值。

### <a name="remarks"></a>备注

使用此运算符可调用对象所指向的类中的方法 `CAutoPtr` 。 在调试版本中，如果指向 NULL，将发生断言失败 `CAutoPtr` 。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr：： operator T *

转换运算符。

```cpp
operator T* () const throw();
```

### <a name="return-value"></a>返回值

返回一个指针，该指针指向在类模板中定义的对象数据类型。

### <a name="example"></a>示例

请参阅[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的示例。

## <a name="see-also"></a>另请参阅

[CHeapPtr 类](../../atl/reference/cheapptr-class.md)<br/>
[CAutoVectorPtr 类](../../atl/reference/cautovectorptr-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
