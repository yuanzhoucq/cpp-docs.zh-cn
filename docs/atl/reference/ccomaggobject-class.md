---
title: "CComAggObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 29
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 386ab09418c879c0de0d82d729a3de1b2e270016
ms.lasthandoff: 02/24/2017

---
# <a name="ccomaggobject-class"></a>CComAggObject 类
此类实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)聚合对象接口。 根据定义，聚集的对象都包含在外部对象。 `CComAggObject`类是类似于[CComObject 类](../../atl/reference/ccomobject-class.md)，只不过它公开可向外部客户端直接访问的接口。  
  
## <a name="syntax"></a>语法  
  
```
template<class contained>  
class CComAggObject : public IUnknown, 
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>参数  
 `contained`  
 您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要在对象上支持任何其他接口也一样。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComAggObject::CComAggObject](#ccomaggobject)|构造函数。|  
|[CComAggObject:: ~ CComAggObject](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComAggObject::AddRef](#addref)|递增上聚合的对象的引用计数。|  
|[CComAggObject::CreateInstance](#createinstance)|此静态函数允许您创建一个新**CComAggObject** `contained` ** > **对象而不需要的开销[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。|  
|[CComAggObject::FinalConstruct](#finalconstruct)|执行的最后一个初始化`m_contained`。|  
|[CComAggObject::FinalRelease](#finalrelease)|执行最终销毁`m_contained`。|  
|[CComAggObject::QueryInterface](#queryinterface)|检索指向所请求的接口的指针。|  
|[CComAggObject::Release](#release)|聚合的对象的引用计数递减。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CComAggObject::m_contained](#m_contained)|委托`IUnknown`对未知的外部对象的调用。|  
  
## <a name="remarks"></a>备注  
 `CComAggObject`实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)聚合对象。 `CComAggObject`都具有其自己**IUnknown**接口，独立于外部对象**IUnknown**接口，并保留其自身的引用计数。  
  
 有关聚合的详细信息，请参阅文章[ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComAggObject`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="addref"></a>CComAggObject::AddRef  
 递增上聚合的对象的引用计数。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 可能是有用的诊断或测试一个值。  
  
##  <a name="ccomaggobject"></a>CComAggObject::CComAggObject  
 构造函数。  
  
```
CComAggObject(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 [in]未知的外部对象。  
  
### <a name="remarks"></a>备注  
 初始化`CComContainedObject`成员， [m_contained](#m_contained)，和模块锁计数递增&1;。  
  
 析构函数递减模块锁计数。  
  
##  <a name="dtor"></a>CComAggObject:: ~ CComAggObject  
 析构函数。  
  
```
~CComAggObject();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源，调用[FinalRelease](#finalrelease)，并减少模块锁计数。  
  
##  <a name="createinstance"></a>CComAggObject::CreateInstance  
 此静态函数允许您创建一个新**CComAggObject** `contained` ** > **对象而不需要的开销[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。  
  
```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```  
  
### <a name="parameters"></a>参数  
 `pp`  
 [out]一个指向**CComAggObject\<***包含* ** > **指针。 如果`CreateInstance`不成功，`pp`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 返回的对象具有引用计数为零，因此请调用`AddRef`立即，然后使用**版本**以完成后释放对对象指针的引用。  
  
 如果执行不需要直接访问对象，但仍想要创建新的对象，而不需要的开销`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)相反。  
  
##  <a name="finalconstruct"></a>CComAggObject::FinalConstruct  
 调用对象构造的最后阶段，此方法对中执行任何最终初始化[m_contained](#m_contained)成员。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="finalrelease"></a>CComAggObject::FinalRelease  
 在对象销毁过程中调用，此方法释放[m_contained](#m_contained)成员。  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComAggObject::m_contained  
 一个[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)从您的类派生的对象。  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>参数  
 `contained`  
 [in]您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要在对象上支持任何其他接口也一样。  
  
### <a name="remarks"></a>备注  
 所有**IUnknown**调用通过`m_contained`委派给未知的外部对象。  
  
##  <a name="queryinterface"></a>CComAggObject::QueryInterface  
 检索指向所请求的接口的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]正在请求的接口的标识符。  
  
 `ppvObject`  
 [out]指向由标识的接口指针的指针`iid`。 如果该对象不支持此接口，`ppvObject`设置为**NULL**。  
  
 `pp`  
 [out]指向由类型标识的接口指针的指针`Q`。 如果该对象不支持此接口，`pp`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 如果所请求的接口是**IUnknown**，`QueryInterface`返回指向聚合对象本身的指针**IUnknown**和递增引用计数。 否则，此方法通过接口会询问`CComContainedObject`成员， [m_contained](#m_contained)。  
  
##  <a name="release"></a>CComAggObject::Release  
 聚合的对象的引用计数递减。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 在调试版本中**版本**返回一个值，可能是有用的诊断或测试。 在非调试生成中，**版本**始终返回 0。  
  
## <a name="see-also"></a>另请参阅  
 [CComObject 类](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](http://msdn.microsoft.com/library/e7e568d7-04e0-4226-b5dc-224deed229ab)   
 [DECLARE_ONLY_AGGREGATABLE](http://msdn.microsoft.com/library/a54220df-4330-4e4d-b7fb-8b63dd62d337)   
 [DECLARE_NOT_AGGREGATABLE](http://msdn.microsoft.com/library/2a116c7c-bab8-4f2a-a9ad-03d7aba0f762)   
 [类概述](../../atl/atl-class-overview.md)

