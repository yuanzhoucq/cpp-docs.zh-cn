---
title: CComEnumImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14c7b1e72db3337b786a0e524ae3d8da964f6bbc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365023"
---
# <a name="ccomenumimpl-class"></a>CComEnumImpl 类
此类提供正在枚举的项数组中的存储位置的 COM 枚举器接口的实现。  
  
## <a name="syntax"></a>语法  
  
```
template <class Base,
    const IID* piid, class T, class Copy>  
class ATL_NO_VTABLE CComEnumImpl : public Base
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 COM 枚举器 ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) 接口。  
  
 `piid`  
 指向的枚举器接口的接口 ID 的指针。  
  
 `T`  
 枚举器接口所显示的项类型。  
  
 `Copy`  
 同类[复制策略类](../../atl/atl-copy-policy-classes.md)。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|构造函数。|  
|[CComEnumImpl:: ~ CComEnumImpl](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComEnumImpl::Clone](#clone)|实现[IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx)。|  
|[CComEnumImpl::Init](#init)|初始化枚举数。|  
|[CComEnumImpl::Next](#next)|实现[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx)。|  
|[CComEnumImpl::Reset](#reset)|实现[IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx)。|  
|[CComEnumImpl::Skip](#skip)|实现[IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx)。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComEnumImpl::m_begin](#m_begin)|指向数组中的第一项的指针。|  
|[CComEnumImpl::m_dwFlags](#m_dwflags)|复制标志传递`Init`。|  
|[CComEnumImpl::m_end](#m_end)|指向刚超出数组中的最后一项的位置的指针。|  
|[CComEnumImpl::m_iter](#m_iter)|指向数组中的当前项的指针。|  
|[CComEnumImpl::m_spUnk](#m_spunk)|**IUnknown**提供所枚举的集合的对象的指针。|  
  
## <a name="remarks"></a>备注  
 `CComEnumImpl` 提供正在枚举的项数组中的存储位置的 COM 枚举器接口的实现。 此类是类似于`IEnumOnSTLImpl`类，该类提供枚举器接口的实现基于 c + + 标准库容器。  
  
> [!NOTE]
>  有关进一步之间的差异的详细信息`CComEnumImpl`和`IEnumOnSTLImpl`，请参阅[CComEnumImpl::Init](#init)。  
  
 通常情况下，将*不*需要来创建你自己的枚举器类派生自此接口的实现。 如果你想要使用基于数组的 ATL 提供枚举，则更常见的是创建的实例[CComEnum](../../atl/reference/ccomenum-class.md)。  
  
 但是，如果你确实需要提供的自定义的枚举器 （例如，一个公开除了枚举器接口的接口），你可以从此类派生。 在此情况下，很可能需要重写[CComEnumImpl::Clone](#clone)方法以提供您自己的实现。  
  
 有关详细信息，请参阅[ATL 集合和枚举数](../../atl/atl-collections-and-enumerators.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `CComEnumImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="ccomenumimpl"></a>  CComEnumImpl::CComEnumImpl  
 构造函数。  
  
```
CComEnumImpl();
```  
  
##  <a name="dtor"></a>  CComEnumImpl:: ~ CComEnumImpl  
 析构函数。  
  
```
~CComEnumImpl();
```  
  
##  <a name="init"></a>  CComEnumImpl::Init  
 将指针传递给任何客户端返回的枚举器接口之前，必须调用此方法。  
  
```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```  
  
### <a name="parameters"></a>参数  
 *begin*  
 指向包含要枚举的项的数组的第一个元素的指针。  
  
 `end`  
 指向刚超出最后一个元素的数组，其中包含要枚举的项的位置的指针。  
  
 *pUnk*  
 [in]**IUnknown**必须保持活动状态的枚举数的生存期内的对象的指针。 传递**NULL**如果不存在任何此类对象。  
  
 `flags`  
 指定应取得所有权的数组或建立一份枚举器的标志。 可能的值如下所述。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 仅一次调用此方法-初始化枚举数，请使用它，然后将其丢弃。  
  
 如果将指针传递给保存在另一个对象数组中的项 （和不要询问枚举器，用于将数据复制），则可以使用*pUnk*参数以确保对象和数组为均可用于只要枚举器需要这些。 枚举器只需包含要保持处于活动状态的对象上的 COM 引用。 枚举数被销毁时自动释放 COM 引用。  
  
 `flags`参数允许你指定枚举器应如何处理传递给它的数组元素。 `flags` 可以执行中的值之一**CComEnumFlags**枚举如下所示：  
  
```  
enum CComEnumFlags  
   {  
   AtlFlagNoCopy = 0,  
   AtlFlagTakeOwnership = 2, // BitOwn  
   AtlFlagCopy = 3           // BitOwn | BitCopy  
   };  
```  
  
 **AtlFlagNoCopy**意味着数组的生存期不控制枚举器。 在这种情况下，其中一个数组将静态或标识的对象*pUnk*将负责在不再需要时释放数组。  
  
 **AtlFlagTakeOwnership**意味着，该数组的析构是为受控枚举器。 在这种情况下，该数组必须具有已动态分配的使用**新**。 枚举数将删除其析构函数中的数组。 通常情况下，将通过**NULL**为*pUnk*，但你仍可以传递有效指针，如果你需要的枚举数析构出于某种原因接收通知。  
  
 **AtlFlagCopy**意味着，一个新数组是由复制传递到的数组来创建`Init`。 新数组的生存期是控制枚举器。 枚举数将删除其析构函数中的数组。 通常情况下，将通过**NULL**为*pUnk*，但你仍可以传递有效指针，如果你需要的枚举数析构出于某种原因接收通知。  
  
> [!NOTE]
>  此方法的原型为类型指定的数组元素**T**，其中**T**被定义为类的模板参数。 这是通过 COM 接口方法公开的相同类型[CComEnumImpl::Next](#next)。 这是，与不同[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)，此类不支持不同的存储，并公开数据类型。 数组中元素的数据类型必须是通过 COM 接口公开的数据类型相同。  
  
##  <a name="clone"></a>  CComEnumImpl::Clone  
 此方法提供的实现[IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx)通过创建类型的对象的方法`CComEnum`，具有相同的数组和迭代器使用的当前对象，初始化它并在返回接口新创建的对象。  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>参数  
 `ppEnum`  
 [out]从当前的枚举器克隆上新创建对象的枚举器接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 请注意，克隆的枚举器永远不会将其自己的原始枚举器使用的数据副本 （或取得所有权）。 如有必要，克隆的枚举器将保持原始枚举器处于活动状态 （使用 COM 引用） 以确保数据可用，只要它们需要它。  
  
##  <a name="m_spunk"></a>  CComEnumImpl::m_spUnk  
 此智能指针保留在传递到的对象的引用[CComEnumImpl::Init](#init)，确保，它将保持活动状态的枚举数的生存期内。  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
##  <a name="m_begin"></a>  CComEnumImpl::m_begin  
 指向刚超出最后一个元素的数组，其中包含要枚举的项的位置的指针。  
  
```
T* m_begin;
```  
  
##  <a name="m_end"></a>  CComEnumImpl::m_end  
 指向包含要枚举的项的数组的第一个元素的指针。  
  
```
T* m_end;
```  
  
##  <a name="m_iter"></a>  CComEnumImpl::m_iter  
 指向数组，其中包含要枚举的项的当前元素的指针。  
  
```
T* m_iter;
```  
  
##  <a name="m_dwflags"></a>  CComEnumImpl::m_dwFlags  
 标志传递给[CComEnumImpl::Init](#init)。  
  
```
DWORD m_dwFlags;
```  
  
##  <a name="next"></a>  CComEnumImpl::Next  
 此方法提供的实现[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx)方法。  
  
```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>参数  
 `celt`  
 [in]请求的元素数目。  
  
 `rgelt`  
 [out]要填充元素的数组。  
  
 `pceltFetched`  
 [out]中实际返回的元素的数目`rgelt`。 这可以是小于`celt`如果少于`celt`元素保持在列表中。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="reset"></a>  CComEnumImpl::Reset  
 此方法提供的实现[IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx)方法。  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="skip"></a>  CComEnumImpl::Skip  
 此方法提供的实现[IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx)方法。  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>参数  
 `celt`  
 [in]要跳过的元素数。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 如果返回 E_INVALIDARG`celt`为零，则返回 S_FALSE 如果小于`celt`返回元素，否则，返回，则为 S_OK。  
  
## <a name="see-also"></a>请参阅  
 [IEnumOnSTLImpl 类](../../atl/reference/ienumonstlimpl-class.md)   
 [CComEnum 类](../../atl/reference/ccomenum-class.md)   
 [类概述](../../atl/atl-class-overview.md)
