---
title: CComPolyObject 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 383a83a2e2b09c9652e7185592a5891179416e0f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364097"
---
# <a name="ccompolyobject-class"></a>CComPolyObject 类
此类实现**IUnknown**聚合或非聚合对象。  
  
## <a name="syntax"></a>语法  
  
```
template<class contained>  
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>参数  
 `contained`  
 你的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持很好地从任何其他接口。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComPolyObject::CComPolyObject](#ccompolyobject)|构造函数。|  
|[CComPolyObject:: ~ CComPolyObject](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComPolyObject::AddRef](#addref)|对象的引用计数递增 1。|  
|[CComPolyObject::CreateInstance](#createinstance)|（静态）允许你创建一个新**CComPolyObject <** `contained` **>** 对象而不需要的开销[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。|  
|[CComPolyObject::FinalConstruct](#finalconstruct)|执行的最终初始化`m_contained`。|  
|[CComPolyObject::FinalRelease](#finalrelease)|执行的最终析构`m_contained`。|  
|[CComPolyObject::QueryInterface](#queryinterface)|检索指向所请求的接口的指针。|  
|[CComPolyObject::Release](#release)|递减对象的引用计数。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComPolyObject::m_contained](#m_contained)|委托**IUnknown**调用到未知的外部对象，如果对象进行了聚合或**IUnknown**如果对象不会聚合的对象。|  
  
## <a name="remarks"></a>备注  
 `CComPolyObject` 实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)聚合或非聚合对象。  
  
 实例时`CComPolyObject`创建的外部值检查未知。 如果它是**NULL**， **IUnknown**为非聚合对象实现。 如果不是未知的外部对象**NULL**， **IUnknown**为聚合对象实现。  
  
 使用的优点`CComPolyObject`是，你可以避免同时[CComAggObject](../../atl/reference/ccomaggobject-class.md)和[CComObject](../../atl/reference/ccomobject-class.md)处理聚合和非聚合情况你模块中。 单个`CComPolyObject`对象处理这两种情况。 这意味着你的模块中存在的 vtable 只有一个副本和函数的一个副本。 如果你 vtable 很大，这会显著降低模块大小。 但是，如果你 vtable 很小，则使用`CComPolyObject`由于未经过优化聚合或非聚合对象，可能会导致稍大一些的模块大小允许进行`CComAggObject`和`CComObject`。  
  
 如果`DECLARE_POLY_AGGREGATABLE`对象的类定义中指定宏`CComPolyObject`将用于创建你的对象。 `DECLARE_POLY_AGGREGATABLE` 会自动将声明为如果你使用 ATL 项目向导创建完全控制或 Internet 资源管理器控件。  
  
 如果聚合，`CComPolyObject`对象都具有其自己**IUnknown**、 独立于外部对象的**IUnknown**，并维护其自己的引用计数。 `CComPolyObject` 使用[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)将委托给未知的外部对象。  
  
 有关聚合的详细信息，请参阅文章[ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="addref"></a>  CComPolyObject::AddRef  
 递增上对象的引用计数。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断或测试。  
  
##  <a name="ccompolyobject"></a>  CComPolyObject::CComPolyObject  
 构造函数。  
  
```
CComPolyObject(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 [in]指向未知的外部对象的对象是否进行聚合，或**NULL**如果对象不会聚合的对象。  
  
### <a name="remarks"></a>备注  
 初始化`CComContainedObject`数据成员[m_contained](#m_contained)，和模块锁计数递增 1。  
  
 析构函数递减模块锁计数。  
  
##  <a name="dtor"></a>  CComPolyObject:: ~ CComPolyObject  
 析构函数。  
  
```
~CComPolyObject();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源，调用[FinalRelease](#finalrelease)，并减少模块锁计数。  
  
##  <a name="createinstance"></a>  CComPolyObject::CreateInstance  
 允许你创建一个新**CComPolyObject <** `contained` **>** 对象而不需要的开销[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
```
static HRESULT WINAPI CreateInstance(  
    LPUNKNOWN pUnkOuter, 
    CComPolyObject<contained>** pp);
```  
  
### <a name="parameters"></a>参数  
 `pp`  
 [out]指向的指针**CComPolyObject <** `contained` **>** 指针。 如果`CreateInstance`不成功，`pp`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 返回的对象具有引用计数为零，因此调用`AddRef`立即，然后使用**版本**以完成后释放对象指针上的引用。  
  
 如果你不需要直接访问的对象，但仍想要创建一个新的对象，而无需开销`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)相反。  
  
##  <a name="finalconstruct"></a>  CComPolyObject::FinalConstruct  
 在对象构造的最终阶段过程中调用，此方法对中执行任何最终初始化[m_contained](#m_contained)数据成员。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="finalrelease"></a>  CComPolyObject::FinalRelease  
 在对象销毁过程中调用，此方法释放[m_contained](#m_contained)数据成员。  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComPolyObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)从您的类派生的对象。  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>参数  
 `contained`  
 [in]你的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持很好地从任何其他接口。  
  
### <a name="remarks"></a>备注  
 **IUnknown**调用通过`m_contained`将委派给未知的外部对象中，如果对象进行了聚合，或到**IUnknown**如果对象不会聚合此对象。  
  
##  <a name="queryinterface"></a>  CComPolyObject::QueryInterface  
 检索指向所请求的接口的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>参数  
 `Q`  
 COM 接口中。  
  
 `iid`  
 [in]所请求的接口的标识符。  
  
 `ppvObject`  
 [out]指向由标识的接口指针的指针`iid`。 如果对象不支持此接口，`ppvObject`设置为**NULL**。  
  
 `pp`  
 [out]指向由标识的接口的指针 **__uuidof(Q)**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 聚合对象，如果所请求的接口是**IUnknown**，`QueryInterface`将指针返回到聚合对象的自己**IUnknown**和递增引用计数。 否则，此方法通过接口会询问`CComContainedObject`数据成员[m_contained](#m_contained)。  
  
##  <a name="release"></a>  CComPolyObject::Release  
 递减引用计数对象上。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 在调试版本中，**版本**返回一个值，可能是用于诊断或测试。 在非调试版本中，**版本**始终返回 0。  
  
## <a name="see-also"></a>请参阅  
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)   
 [类概述](../../atl/atl-class-overview.md)
