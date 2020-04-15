---
title: CComEnumImpl 类
ms.date: 11/04/2016
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
helpviewer_keywords:
- CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
ms.openlocfilehash: 965e0a8bf6c890882754b60e2785832933d1c52c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327866"
---
# <a name="ccomenumimpl-class"></a>CComEnumImpl 类

此类提供 COM 枚举器接口的实现，其中枚举的项存储在数组中。

## <a name="syntax"></a>语法

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>参数

*基地*<br/>
COM 枚举器接口。 有关示例，请参阅[IEnumString。](/windows/win32/api/objidl/nn-objidl-ienumstring)

*皮伊德*<br/>
指向枚举器接口接口的接口 ID 的指针。

*T*<br/>
枚举器接口公开的项的类型。

*复制*<br/>
同质[复制策略类](../../atl/atl-copy-policy-classes.md)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComenumimpl：ccomEnumimpl](#ccomenumimpl)|构造函数。|
|[CComenumimpl：：_CComEnumimpl](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComEnumimpl：克隆](#clone)|**克隆**枚举接口方法的实现。|
|[CComenumimpl：：Init](#init)|初始化枚举器。|
|[CComEnumimpl：：下一个](#next)|下**一步**的实施。|
|[CComEnumimpl：：重置](#reset)|**复位**的实现。|
|[CComEnumimpl：：跳过](#skip)|**Skip**的实现。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComEnumimpl：：m_begin](#m_begin)|指向数组中第一个项的指针。|
|[CComEnumimpl：m_dwFlags](#m_dwflags)|复制通过`Init`的标志。|
|[CComEnumimpl：m_end](#m_end)|指向数组中最后一个项之外的位置的指针。|
|[CComEnumimpl：m_iter](#m_iter)|指向数组中当前项的指针。|
|[CComEnumimpl：m_spUnk](#m_spunk)|提供`IUnknown`要枚举的集合的对象的指针。|

## <a name="remarks"></a>备注

有关方法实现的示例，请参阅[IEnumString。](/windows/win32/api/objidl/nn-objidl-ienumstring) `CComEnumImpl`提供 COM 枚举器接口的实现，其中枚举的项存储在数组中。 此类类似于类`IEnumOnSTLImpl`，该类提供基于C++标准库容器的枚举器接口的实现。

> [!NOTE]
> 有关 和`CComEnumImpl``IEnumOnSTLImpl`之间的进一步差异的详细信息，请参阅[CComEnumImpl：：init](#init)。

通常，不需要通过*not*派生此接口实现创建自己的枚举器类。 如果要使用基于数组的 ATL 提供的枚举器，则创建[CComEnum](../../atl/reference/ccomenum-class.md)的实例更为常见。

但是，如果确实需要提供自定义枚举器（例如，除了枚举器接口外公开接口），则可以从此类派生。 在此情况下，您可能需要重写[CComEnumImpl：：Clone](#clone)方法来提供您自己的实现。

有关详细信息，请参阅[ATL 集合和枚举器](../../atl/atl-collections-and-enumerators.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComEnumImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>CComenumimpl：ccomEnumimpl

构造函数。

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>CComenumimpl：：_CComEnumimpl

析构函数。

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>CComenumimpl：：Init

在将指向枚举器接口的指针传回任何客户端之前，必须调用此方法。

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>参数

*开始*<br/>
指向数组的第一个元素的指针，其中包含要枚举的项。

*结束*<br/>
指向数组最后一个元素的位置的指针，其中包含要枚举的项。

*朋 克*<br/>
[在]在`IUnknown`枚举器的生存期内必须保持活动的对象的指针。 如果不存在此类对象，则传递 NULL。

*标志*<br/>
指示枚举器是否应取得数组的所有权或复制数组的标志。 下面将介绍可能的值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

只调用此方法一次 - 初始化枚举器，使用它，然后扔掉它。

如果将指针传递给另一个对象中保留的数组中的项（并且不要求枚举器复制数据），则可以使用*pUnk*参数确保对象及其持有的数组在枚举器需要时可用。 枚举器只需在对象上保存 COM 引用，即可使其保持活动状态。 销毁枚举器时，将自动释放 COM 引用。

*标志*参数允许您指定枚举器应如何处理传递给它的数组元素。 *标志*可以从下面所示的`CComEnumFlags`枚举中获取其中一个值：

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`表示数组的生存期不受枚举器控制。 在这种情况下，数组将是静态的，或者*pUnk*标识的对象将负责在不再需要数组时释放数组。

`AtlFlagTakeOwnership`表示数组的销毁由枚举器控制。 在这种情况下，数组必须使用**new**进行动态分配。 枚举器将删除其析构函数中的数组。 通常，您将传递*pUnk*的 NULL，尽管如果您由于某种原因需要通知枚举器的销毁，您仍然可以传递有效的指针。

`AtlFlagCopy`表示要通过复制传递给`Init`的数组来创建新数组。 新数组的生存期将由枚举器控制。 枚举器将删除其析构函数中的数组。 通常，您将传递*pUnk*的 NULL，尽管如果您由于某种原因需要通知枚举器的销毁，您仍然可以传递有效的指针。

> [!NOTE]
> 此方法的原型将数组元素指定为类型`T`，其中`T`定义为类的模板参数。 这是通过 COM 接口方法[CComEnumImpl：：：next](#next)公开的相同类型。 这意味着，与[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)不同，此类不支持不同的存储和公开数据类型。 数组中元素的数据类型必须与通过 COM 接口公开的数据类型相同。

## <a name="ccomenumimplclone"></a><a name="clone"></a>CComEnumimpl：克隆

此方法通过创建类型`CComEnum`对象、使用当前对象使用的相同数组和迭代器初始化它，并在新创建的对象上返回接口来提供**Clone**方法的实现。

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>参数

*普埃纳姆*<br/>
[出]从当前枚举器克隆的新创建对象的枚举器接口。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

请注意，克隆的枚举者永远不会自行复制（或取得原始枚举器使用的数据的所有权）。 如有必要，克隆的枚举器将保持原始枚举器处于活动状态（使用 COM 引用），以确保数据在需要时可用。

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>CComEnumimpl：m_spUnk

此智能指针维护传递给[CComEnumImpl：：init](#init)的对象的引用，确保它在枚举器的生存期内保持活动状态。

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>CComEnumimpl：：m_begin

指向数组最后一个元素的位置的指针，其中包含要枚举的项。

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>CComEnumimpl：m_end

指向数组的第一个元素的指针，其中包含要枚举的项。

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>CComEnumimpl：m_iter

指向数组的当前元素的指针，其中包含要枚举的项。

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>CComEnumimpl：m_dwFlags

旗子传递给[CComEnumImpl：init。](#init)

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>CComEnumimpl：：下一个

此方法提供**Next**方法的实现。

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>参数

*celt*<br/>
[在]请求的元素数。

*格尔特*<br/>
[出]要填充的元素的数组。

*pceltFetched*<br/>
[出]在*rgelt*中实际返回的元素数。 如果列表中保留的小于*celt*元素，则这可能小于*celt。*

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ccomenumimplreset"></a><a name="reset"></a>CComEnumimpl：：重置

此方法提供**重置**方法的实现。

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ccomenumimplskip"></a><a name="skip"></a>CComEnumimpl：：跳过

此方法提供**Skip**方法的实现。

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>参数

*celt*<br/>
[在]要跳过的元素数。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

如果*celt*为零，则返回E_INVALIDARG，如果返回小于*celt*元素，则返回S_FALSE返回，否则返回S_OK。

## <a name="see-also"></a>另请参阅

[IEnumOnSTLImpl 类](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum 类](../../atl/reference/ccomenum-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
