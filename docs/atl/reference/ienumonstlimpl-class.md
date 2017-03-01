---
title: "IEnumOnSTLImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IEnumOnSTLImpl
- ATL.IEnumOnSTLImpl
- ATL::IEnumOnSTLImpl
dev_langs:
- C++
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 291993d2914d6082b69bfe7816d7c805e93494c4
ms.lasthandoff: 02/24/2017

---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl 类
此类定义一个基于 c + + 标准库集合的枚举器接口。  
  
## <a name="syntax"></a>语法  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>  
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 COM 枚举器 ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) 接口。  
  
 `piid`  
 指向的枚举器接口的接口 ID 的指针。  
  
 `T`  
 枚举器接口所显示的项的类型。  
  
 `Copy`  
 一个[复制策略类](../../atl/atl-copy-policy-classes.md)。  
  
 `CollType`  
 C + + 标准库容器类。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IEnumOnSTLImpl::Clone](#clone)|实现[IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx)。|  
|[IEnumOnSTLImpl::Init](#init)|初始化枚举器。|  
|[IEnumOnSTLImpl::Next](#next)|实现[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx)。|  
|[IEnumOnSTLImpl::Reset](#reset)|实现[IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx)。|  
|[IEnumOnSTLImpl::Skip](#skip)|实现[IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx)。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[IEnumOnSTLImpl::m_iter](#m_iter)|表示集合中的枚举器的当前位置迭代器。|  
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|指向 c + + 标准库容器保存要枚举的项的指针。|  
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|**IUnknown**提供集合的对象的指针。|  
  
## <a name="remarks"></a>备注  
 `IEnumOnSTLImpl`提供了正在枚举项目兼容的 c + + 标准库容器中的存储在何处 COM 枚举器接口的实现。 此类是类似于[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)类，该类提供的枚举器接口的实现基于数组。  
  
> [!NOTE]
>  请参阅[CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init)有关进一步之间的差异的详细信息`CComEnumImpl`和`IEnumOnSTLImpl`。  
  
 通常情况下，将*不*需要通过此接口的实现从派生来创建您自己的枚举器类。 如果您想要使用基于 c + + 标准库容器的 ATL 提供的枚举器，则更常见的是创建的实例[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)，或创建通过派生自返回一个枚举器的集合类[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)。  
  
 但是，如果您确实需要以提供自定义枚举器 （例如，一种公开除了枚举器接口的接口），您可以从此类派生。 在这种情况很可能需要重写[克隆](#clone)方法以提供您自己的实现。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `IEnumOnSTLImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-nameinita--ienumonstlimplinit"></a><a name="init"></a>IEnumOnSTLImpl::Init  
 初始化枚举器。  
  
```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```  
  
### <a name="parameters"></a>参数  
 `pUnkForRelease`  
 [in]**IUnknown**必须保持活动状态的枚举器的生存期内的对象的指针。 传递**NULL**如果不存在任何此类对象。  
  
 `collection`  
 对包含要枚举的项目的 c + + 标准库容器的引用。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 如果您通过`Init`对集合的引用保存在另一个对象，您可以使用`pUnkForRelease`参数，以确保该对象和它包含的集合是可用于，只要枚举器需要它。  
  
 将指针传递给枚举器接口返回到任何客户端之前，必须调用此方法。  
  
##  <a name="a-nameclonea--ienumonstlimplclone"></a><a name="clone"></a>IEnumOnSTLImpl::Clone  
 此方法将提供的实现[IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx)通过创建类型的对象的方法`CComEnumOnSTL`，具有相同的集合和当前对象所使用的迭代器对其进行初始化并返回新创建的对象的接口。  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>参数  
 `ppEnum`  
 [out]从当前的枚举数克隆上新创建的对象的枚举器接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="a-namemspunka--ienumonstlimplmspunk"></a><a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk  
 **IUnknown**提供集合的对象的指针。  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
### <a name="remarks"></a>备注  
 此智能指针保持对传递给该对象的引用[IEnumOnSTLImpl::Init](#init)，确保它仍然保持活动状态的枚举器的生存期内。  
  
##  <a name="a-namempcollectiona--ienumonstlimplmpcollection"></a><a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection  
 此成员将指向提供推动枚举器接口的实现的数据的集合。  
  
```
CollType* m_pcollection;
```  
  
### <a name="remarks"></a>备注  
 此成员初始化调用[IEnumOnSTLImpl::Init](#init)。  
  
##  <a name="a-namemitera--ienumonstlimplmiter"></a><a name="m_iter"></a>IEnumOnSTLImpl::m_iter  
 此成员将具有用来标记该集合中的当前位置并定位到后续元素的迭代器。  
  
```
CollType::iterator m_iter;
```  
  
##  <a name="a-namenexta--ienumonstlimplnext"></a><a name="next"></a>IEnumOnSTLImpl::Next  
 此方法将提供的实现[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx)方法。  
  
```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>参数  
 `celt`  
 [in]请求的元素数。  
  
 `rgelt`  
 [out]要使用元素来填充的数组。  
  
 `pceltFetched`  
 [out]中实际返回的元素数目`rgelt`。 这可能是小于`celt`如果少于`celt`元素都将保留在列表中。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="a-namereseta--ienumonstlimplreset"></a><a name="reset"></a>IEnumOnSTLImpl::Reset  
 此方法将提供的实现[IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx)方法。  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="a-nameskipa--ienumonstlimplskip"></a><a name="skip"></a>IEnumOnSTLImpl::Skip  
 此方法将提供的实现[IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx)方法。  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>参数  
 `celt`  
 [in]要跳过的元素数。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

