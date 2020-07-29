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
ms.openlocfilehash: 517a4e90ca21e22dcf161aefcff61a40437eabe0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226602"
---
# <a name="ccomenumimpl-class"></a>CComEnumImpl 类

此类提供 COM 枚举器接口的实现，其中所枚举的项存储在数组中。

## <a name="syntax"></a>语法

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>参数

*基座*<br/>
COM 枚举器接口。 有关示例，请参阅[IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 。

*piid*<br/>
指向枚举器接口的接口 ID 的指针。

*T*<br/>
枚举器接口公开的项的类型。

*复制*<br/>
同类[复制策略类](../../atl/atl-copy-policy-classes.md)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|构造函数。|
|[CComEnumImpl：： ~ CComEnumImpl](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CComEnumImpl：： Clone](#clone)|**克隆**枚举接口方法的实现。|
|[CComEnumImpl：： Init](#init)|初始化枚举器。|
|[CComEnumImpl：： Next](#next)|**下一步**的实现。|
|[CComEnumImpl：： Reset](#reset)|**重置**的实现。|
|[CComEnumImpl：： Skip](#skip)|**Skip**的实现。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComEnumImpl：： m_begin](#m_begin)|指向数组中第一个项的指针。|
|[CComEnumImpl：： m_dwFlags](#m_dwflags)|复制传递的标志 `Init` 。|
|[CComEnumImpl：： m_end](#m_end)|指向刚超出数组中最后一项的位置的指针。|
|[CComEnumImpl：： m_iter](#m_iter)|指向数组中的当前项的指针。|
|[CComEnumImpl：： m_spUnk](#m_spunk)|`IUnknown`提供要枚举的集合的对象的指针。|

## <a name="remarks"></a>备注

有关方法实现的示例，请参阅[IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 。 `CComEnumImpl`提供 COM 枚举器接口的实现，其中所枚举的项存储在数组中。 此类与 `IEnumOnSTLImpl` 类相似，该类提供基于 c + + 标准库容器的枚举器接口的实现。

> [!NOTE]
> 有关和之间的进一步差异的详细信息 `CComEnumImpl` `IEnumOnSTLImpl` ，请参阅[CComEnumImpl：： Init](#init)。

通常，您*不*需要通过从此接口实现派生来创建自己的枚举器类。 如果要使用基于数组的基于 ATL 的枚举器，则创建[CComEnum](../../atl/reference/ccomenum-class.md)的实例较为常见。

但是，如果确实需要提供自定义枚举器（例如，除了枚举器接口外，还需要提供接口），可以从此类派生。 在这种情况下，可能需要重写[CComEnumImpl：： Clone](#clone)方法才能提供自己的实现。

有关详细信息，请参阅[ATL 集合和枚举](../../atl/atl-collections-and-enumerators.md)器。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Base`

`CComEnumImpl`

## <a name="requirements"></a>要求

**标头：** atlcom。h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl

构造函数。

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>CComEnumImpl：： ~ CComEnumImpl

析构函数。

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>CComEnumImpl：： Init

必须先调用此方法，然后再将指向枚举器接口的指针传递回任何客户端。

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>参数

*准备*<br/>
指向包含要枚举的项的数组的第一个元素的指针。

*end*<br/>
指向刚超出数组最后一个元素的位置的指针，该数组包含要枚举的项。

*pUnk*<br/>
中`IUnknown`必须在枚举器的生存期内保持活动状态的对象的指针。 如果不存在此类对象，则传递 NULL。

*flag*<br/>
指定枚举器是应取得数组的所有权还是创建它的副本的标志。 可能的值如下所述。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

仅调用此方法一次—初始化枚举器，使用它，然后将其丢弃。

如果将指向数组中的项的指针传递到另一个对象中，而不要求枚举器复制数据，则可以使用 PUnk 参数来确保只要枚举器需要，就可以使用*pUnk*参数来确保该对象及其包含的数组。 枚举器仅保存对对象的 COM 引用，以使其保持活动状态。 当枚举器被销毁时，将自动释放 COM 引用。

*Flags*参数用于指定枚举器应如何处理传递给它的数组元素。 *标志*可采用下面所示的枚举中的值之一 `CComEnumFlags` ：

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`表示数组的生存期不由枚举器控制。 在这种情况下，该数组将为静态，或者由*pUnk*标识的对象将负责在不再需要该数组时将其释放。

`AtlFlagTakeOwnership`表示将由枚举器控制对数组的析构。 在这种情况下，必须使用动态分配数组 **`new`** 。 枚举器将在其析构函数中删除数组。 通常情况下，你将为*pUnk*传递 NULL，不过，如果你出于某种原因需要通知枚举器，则仍可传递有效指针。

`AtlFlagCopy`表示将通过复制传递到的数组来创建新的数组 `Init` 。 新数组的生存期由枚举器控制。 枚举器将在其析构函数中删除数组。 通常情况下，你将为*pUnk*传递 NULL，不过，如果你出于某种原因需要通知枚举器，则仍可传递有效指针。

> [!NOTE]
> 此方法的原型将数组元素指定为类型 `T` ，其中 `T` 定义为类的模板参数。 此类型与通过 COM 接口方法[CComEnumImpl：： Next](#next)公开的类型相同。 这意味着，与[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)不同，此类不支持不同的存储和公开的数据类型。 数组中元素的数据类型必须与通过 COM 接口公开的数据类型相同。

## <a name="ccomenumimplclone"></a><a name="clone"></a>CComEnumImpl：： Clone

此方法通过创建类型为的**Clone**对象 `CComEnum` ，并使用当前对象所使用的相同数组和迭代器对其进行初始化，并返回新创建的对象上的接口，来提供 Clone 方法的实现。

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>参数

*ppEnum*<br/>
弄从当前枚举器克隆的新创建对象上的枚举器接口。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

请注意，克隆的枚举器从不会生成原始枚举器使用的数据的副本（或取得所有权）。 如有必要，克隆的枚举器将使原始枚举器保持活动状态（使用 COM 引用），以确保数据在需要时可供使用。

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>CComEnumImpl：： m_spUnk

此智能指针维护对传递给[CComEnumImpl：： Init](#init)的对象的引用，确保它在枚举器的生存期内保持活动状态。

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>CComEnumImpl：： m_begin

指向刚超出数组最后一个元素的位置的指针，该数组包含要枚举的项。

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>CComEnumImpl：： m_end

指向包含要枚举的项的数组的第一个元素的指针。

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>CComEnumImpl：： m_iter

一个指针，指向包含要枚举的项的数组的当前元素。

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>CComEnumImpl：： m_dwFlags

传递给[CComEnumImpl：： Init](#init)的标志。

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>CComEnumImpl：： Next

此方法提供了**下一**方法的实现。

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>参数

*celt*<br/>
中请求的元素的数目。

*rgelt*<br/>
弄要用元素填充的数组。

*pceltFetched*<br/>
弄在*rgelt*中实际返回的元素数。 如果列表中保留的元素少于*celt* ，则此项可以小于*celt* 。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

## <a name="ccomenumimplreset"></a><a name="reset"></a>CComEnumImpl：： Reset

此方法提供**Reset**方法的实现。

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

## <a name="ccomenumimplskip"></a><a name="skip"></a>CComEnumImpl：： Skip

此方法提供**Skip**方法的实现。

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>参数

*celt*<br/>
中要跳过的元素的数目。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

返回 E_INVALIDARG 如果*celt*为零，则返回 S_FALSE 如果返回小于*celt*的元素，则返回 S_OK; 否则返回。

## <a name="see-also"></a>另请参阅

[IEnumOnSTLImpl 类](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum 类](../../atl/reference/ccomenum-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
