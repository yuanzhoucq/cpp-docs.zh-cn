---
title: IEnumOnSTLImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15f0b26c5c86d023d98d6a13e6b92518756a3179
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206201"
---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl 类
此类定义基于 c + + 标准库集合的枚举器接口。  
  
## <a name="syntax"></a>语法  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>  
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```  
  
#### <a name="parameters"></a>参数  
 *基本*  
 COM 的枚举器。 请参阅[IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring)有关的示例。
  
 *piid*  
 一个指向枚举器接口的接口 ID。  
  
 *T*  
 枚举器接口所显示的项的类型。  
  
 *复制*  
 一个[复制策略类](../../atl/atl-copy-policy-classes.md)。  
  
 *CollType*  
 C + + 标准库容器类。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IEnumOnSTLImpl::Clone](#clone)|实现**克隆**。|  
|[IEnumOnSTLImpl::Init](#init)|初始化枚举器。|  
|[IEnumOnSTLImpl::Next](#next)|实现**下一步**。|  
|[IEnumOnSTLImpl::Reset](#reset)|实现**重置**。|  
|[IEnumOnSTLImpl::Skip](#skip)|实现**跳过**。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[IEnumOnSTLImpl::m_iter](#m_iter)|迭代器，表示集合中的枚举器的当前位置。|  
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|指向 c + + 标准库容器保存要枚举的项的指针。|  
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|`IUnknown`提供集合的对象的指针。|  
  
## <a name="remarks"></a>备注  
 `IEnumOnSTLImpl` 提供要枚举的项在兼容的 c + + 标准库容器中的存储位置的 COM 枚举器接口的实现。 此类是类似于[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)类，该类提供的枚举器接口的实现基于数组。  
  
> [!NOTE]
>  请参阅[CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init)有关进一步之间的差异的详细信息`CComEnumImpl`和`IEnumOnSTLImpl`。  
  
 通常情况下，将*不*需要通过此接口实现从派生来创建您自己的枚举器类。 如果你想要使用基于 c + + 标准库容器的 ATL 提供的枚举器，则更常见的是创建的实例[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)，或创建一个集合类，返回一个枚举器通过派生自[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)。  
  
 但是，如果需要提供的自定义枚举器 （例如，一个公开的枚举数接口除了接口），您可以从此类派生。 在此情况下很可能需要重写[克隆](#clone)方法以提供您自己的实现。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `IEnumOnSTLImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="init"></a>  IEnumOnSTLImpl::Init  
 初始化枚举器。  
  
```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```  
  
### <a name="parameters"></a>参数  
 *pUnkForRelease*  
 [in]`IUnknown`必须保持活动状态的枚举器的生命周期内的对象的指针。 如果没有此类对象存在，则传递 NULL。  
  
 collection  
 对包含要枚举的项的 c + + 标准库容器的引用。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 如果传递`Init`对集合的引用保存在另一个对象，您可以使用*pUnkForRelease*参数以确保对象，并且它包含的集合是可用于为枚举器需要它。  
  
 将指针传递到返回到任何客户端的枚举数接口前，必须调用此方法。  
  
##  <a name="clone"></a>  IEnumOnSTLImpl::Clone  
 此方法提供的实现**克隆**方法通过创建类型的对象`CComEnumOnSTL`，具有相同的集合和迭代器使用的当前对象，初始化并返回该接口上新创建的对象。  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>参数  
 *ppEnum*  
 [out]从当前枚举数中克隆上新创建的对象的枚举器接口。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。  
  
##  <a name="m_spunk"></a>  IEnumOnSTLImpl::m_spUnk  
 `IUnknown`提供集合的对象的指针。  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
### <a name="remarks"></a>备注  
 此智能指针将保留在传递到的对象的引用[IEnumOnSTLImpl::Init](#init)，确保它仍然保持活动状态的枚举器的生存期内。  
  
##  <a name="m_pcollection"></a>  IEnumOnSTLImpl::m_pcollection  
 此成员是指向提供数据驱动的枚举数接口的实现的集合。  
  
```
CollType* m_pcollection;
```  
  
### <a name="remarks"></a>备注  
 此成员初始化通过调用[IEnumOnSTLImpl::Init](#init)。  
  
##  <a name="m_iter"></a>  IEnumOnSTLImpl::m_iter  
 此成员保留用于将标记集合中的当前位置，并导航到后续元素的迭代器。  
  
```
CollType::iterator m_iter;
```  
  
##  <a name="next"></a>  IEnumOnSTLImpl::Next  
 此方法提供的实现**下一步**方法。  
  
```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>参数  
 *celt*  
 [in]请求的元素数。  
  
 *rgelt*  
 [out]要填充元素的数组。  
  
 *pceltFetched*  
 [out]中实际返回的元素数*rgelt*。 这可以是小于*celt*如果少于*celt*列表中剩余的元素。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。  
  
##  <a name="reset"></a>  IEnumOnSTLImpl::Reset  
 此方法提供的实现**重置**方法。  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。  
  
##  <a name="skip"></a>  IEnumOnSTLImpl::Skip  
 此方法提供的实现**跳过**方法。  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>参数  
 *celt*  
 [in]要跳过的元素数。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
