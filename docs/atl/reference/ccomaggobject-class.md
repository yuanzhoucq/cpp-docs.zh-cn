---
title: CComAggObject 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 426a01c1957b276174b8b36884605b69dd501de8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ccomaggobject-class"></a>CComAggObject 类
此类实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)聚合对象的接口。 根据定义，聚合的对象将包含在外部对象。 `CComAggObject`类是类似于[CComObject 类](../../atl/reference/ccomobject-class.md)，只不过它公开一个接口，可直接访问外部客户端。  
  
## <a name="syntax"></a>语法  
  
```
template<class contained>  
class CComAggObject : public IUnknown, 
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>参数  
 `contained`  
 你的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持很好地从任何其他接口。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComAggObject::CComAggObject](#ccomaggobject)|构造函数。|  
|[CComAggObject:: ~ CComAggObject](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComAggObject::AddRef](#addref)|递增上聚合的对象的引用计数。|  
|[CComAggObject::CreateInstance](#createinstance)|此静态函数使你可以创建一个新**CComAggObject <** `contained` **>** 对象而不需要的开销[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。|  
|[CComAggObject::FinalConstruct](#finalconstruct)|执行的最终初始化`m_contained`。|  
|[CComAggObject::FinalRelease](#finalrelease)|执行的最终析构`m_contained`。|  
|[CComAggObject::QueryInterface](#queryinterface)|检索指向所请求的接口的指针。|  
|[CComAggObject::Release](#release)|递减引用计数聚合对象上。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComAggObject::m_contained](#m_contained)|委托`IUnknown`对未知的外部对象的调用。|  
  
## <a name="remarks"></a>备注  
 `CComAggObject` 实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)聚合对象。 `CComAggObject` 具有其自己**IUnknown**接口，独立于外部对象的**IUnknown**接口，并维护其自己的引用计数。  
  
 有关聚合的详细信息，请参阅文章[ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComAggObject`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="addref"></a>  CComAggObject::AddRef  
 递增上聚合的对象的引用计数。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断或测试。  
  
##  <a name="ccomaggobject"></a>  CComAggObject::CComAggObject  
 构造函数。  
  
```
CComAggObject(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 [in]未知的外部对象。  
  
### <a name="remarks"></a>备注  
 初始化`CComContainedObject`成员， [m_contained](#m_contained)，和模块锁计数递增 1。  
  
 析构函数递减模块锁计数。  
  
##  <a name="dtor"></a>  CComAggObject:: ~ CComAggObject  
 析构函数。  
  
```
~CComAggObject();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源，调用[FinalRelease](#finalrelease)，并减少模块锁计数。  
  
##  <a name="createinstance"></a>  CComAggObject::CreateInstance  
 此静态函数使你可以创建一个新**CComAggObject <** `contained` **>** 对象而不需要的开销[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```  
  
### <a name="parameters"></a>参数  
 `pp`  
 [out]一个指向 **CComAggObject\<* * * 包含* **>** 指针。 如果`CreateInstance`不成功，`pp`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 返回的对象具有引用计数为零，因此调用`AddRef`立即，然后使用**版本**以完成后释放对象指针上的引用。  
  
 如果不执行需要直接访问的对象，但仍想要创建一个新的对象，而无需开销`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)相反。  
  
##  <a name="finalconstruct"></a>  CComAggObject::FinalConstruct  
 在对象构造的最终阶段过程中调用，此方法对中执行任何最终初始化[m_contained](#m_contained)成员。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="finalrelease"></a>  CComAggObject::FinalRelease  
 在对象销毁过程中调用，此方法释放[m_contained](#m_contained)成员。  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComAggObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)从您的类派生的对象。  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>参数  
 `contained`  
 [in]你的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持很好地从任何其他接口。  
  
### <a name="remarks"></a>备注  
 所有**IUnknown**调用通过`m_contained`委派给未知的外部对象。  
  
##  <a name="queryinterface"></a>  CComAggObject::QueryInterface  
 检索指向所请求的接口的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]所请求的接口的标识符。  
  
 `ppvObject`  
 [out]指向由标识的接口指针的指针`iid`。 如果对象不支持此接口，`ppvObject`设置为**NULL**。  
  
 `pp`  
 [out]指向由类型标识的接口指针的指针`Q`。 如果对象不支持此接口，`pp`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 如果所请求的接口是**IUnknown**，`QueryInterface`将指针返回到聚合对象的自己**IUnknown**和递增引用计数。 否则，此方法通过接口会询问`CComContainedObject`成员， [m_contained](#m_contained)。  
  
##  <a name="release"></a>  CComAggObject::Release  
 递减引用计数聚合对象上。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 在调试版本中，**版本**返回一个值，可能是用于诊断或测试。 在非调试版本中，**版本**始终返回 0。  
  
## <a name="see-also"></a>请参阅  
 [CComObject 类](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [类概述](../../atl/atl-class-overview.md)
