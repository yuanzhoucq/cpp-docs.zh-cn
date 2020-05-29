---
title: IEnumOnSTLImpl 类
ms.date: 11/04/2016
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
ms.openlocfilehash: 2fbe6ccfbea2836c42a054da7ea9ebeac4e1555d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329710"
---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl 类

此类基于C++标准库集合定义枚举器接口。

## <a name="syntax"></a>语法

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>参数

*基地*<br/>
COM 枚举器。 有关示例，请参阅[IEnumString。](/windows/win32/api/objidl/nn-objidl-ienumstring)

*皮伊德*<br/>
指向枚举器接口接口的接口 ID 的指针。

*T*<br/>
枚举器接口公开的项的类型。

*复制*<br/>
[复制策略类](../../atl/atl-copy-policy-classes.md)。

*拼贴*<br/>
C++标准库容器类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IEnumonSTLimpl：：克隆](#clone)|**克隆**的实现。|
|[IEnumonSTLimpl：：Init](#init)|初始化枚举器。|
|[IEnumonSTLimpl：：下一个](#next)|下**一步**的实施。|
|[IEnumonSTLimpl：：重置](#reset)|**复位**的实现。|
|[IEnumonSTLimpl：：跳过](#skip)|**Skip**的实现。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[IEnumonSTLimpl：：m_iter](#m_iter)|表示枚举器在集合中的当前位置的迭代器。|
|[IEnumonSTLimpl：：m_pcollection](#m_pcollection)|指向C++标准库容器的指针，该容器包含要枚举的项目。|
|[IEnumonSTLimpl：：m_spUnk](#m_spunk)|提供`IUnknown`集合的对象的指针。|

## <a name="remarks"></a>备注

`IEnumOnSTLImpl`提供 COM 枚举器接口的实现，其中枚举的项目存储在与标准库兼容的C++容器中。 此类类似于[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)类，该类为基于数组的枚举器接口提供了实现。

> [!NOTE]
> 请参阅[CComEnumImpl：：init](../../atl/reference/ccomenumimpl-class.md#init)有关 和`CComEnumImpl``IEnumOnSTLImpl`之间的进一步差异的详细信息。

通常，不需要通过*not*派生此接口实现创建自己的枚举器类。 如果要使用基于C++标准库容器的 ATL 提供的枚举器，则更常见的是创建[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)实例，或者创建一个集合类，该集合类通过派生自[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)来返回枚举器。

但是，如果确实需要提供自定义枚举器（例如，除了枚举器接口外公开接口），则可以从此类派生。 在此情况下，您可能需要重写[Clone](#clone)方法以提供您自己的实现。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ienumonstlimplinit"></a><a name="init"></a>IEnumonSTLimpl：：Init

初始化枚举器。

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>参数

*pUnkfor 释放*<br/>
[在]在`IUnknown`枚举器的生存期内必须保持活动的对象的指针。 如果不存在此类对象，则传递 NULL。

*收集*<br/>
对保存要枚举的项目C++标准库容器的引用。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

如果传递`Init`对另一个对象中保存的集合的引用，则可以使用*pUnkForRelease*参数来确保只要枚举器需要，该对象及其保留的集合就可用。

在将指向枚举器接口的指针传回任何客户端之前，必须调用此方法。

## <a name="ienumonstlimplclone"></a><a name="clone"></a>IEnumonSTLimpl：：克隆

此方法通过创建类型`CComEnumOnSTL`对象、使用当前对象使用的相同集合和迭代器初始化它，并在新创建的对象上返回接口来提供**Clone**方法的实现。

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>参数

*普埃纳姆*<br/>
[出]从当前枚举器克隆的新创建对象的枚举器接口。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ienumonstlimplm_spunk"></a><a name="m_spunk"></a>IEnumonSTLimpl：：m_spUnk

提供`IUnknown`集合的对象的指针。

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>备注

此智能指针维护传递给[IEnumOnSTLImpl：：init](#init)的对象的引用，确保它在枚举器的生存期内保持活动状态。

## <a name="ienumonstlimplm_pcollection"></a><a name="m_pcollection"></a>IEnumonSTLimpl：：m_pcollection

此成员指向提供推动实现枚举器接口的数据的集合。

```
CollType* m_pcollection;
```

### <a name="remarks"></a>备注

此成员通过调用[IEnumOnSTLImpl：：Init](#init)初始化。

## <a name="ienumonstlimplm_iter"></a><a name="m_iter"></a>IEnumonSTLimpl：：m_iter

此成员持有用于标记集合中的当前位置并导航到后续元素的迭代器。

```
CollType::iterator m_iter;
```

## <a name="ienumonstlimplnext"></a><a name="next"></a>IEnumonSTLimpl：：下一个

此方法提供**Next**方法的实现。

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>参数

*celt*<br/>
[在]请求的元素数。

*格尔特*<br/>
[出]要用元素填充的数组。

*pceltFetched*<br/>
[出]在*rgelt*中实际返回的元素数。 如果列表中保留少于*celt*元素，则这可能小于*celt。*

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ienumonstlimplreset"></a><a name="reset"></a>IEnumonSTLimpl：：重置

此方法提供**重置**方法的实现。

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ienumonstlimplskip"></a><a name="skip"></a>IEnumonSTLimpl：：跳过

此方法提供**Skip**方法的实现。

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>参数

*celt*<br/>
[在]要跳过的元素数。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
