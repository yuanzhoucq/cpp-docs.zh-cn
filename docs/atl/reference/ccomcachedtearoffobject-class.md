---
title: CComCachedTearOffObject 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62ed04d8e54e4bf107ae12b9a4165b663c9d10d8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203866"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject 类
此类实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)分离式接口。  
  
## <a name="syntax"></a>语法  
  
```
template
 <class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
 ::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>参数  
 `contained`  
 分离式类，派生自`CComTearOffObjectBase`和希望分离式对象以支持接口。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|构造函数。|  
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::AddRef](#addref)|递增引用计数为`CComCachedTearOffObject`对象。|  
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|调用`m_contained::FinalConstruct`（分离式类的方法）。|  
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|调用`m_contained::FinalRelease`（分离式类的方法）。|  
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|返回一个指向`IUnknown`的`CComCachedTearOffObject`对象，或与你分离式的类上的请求接口 (类`contained`)。|  
|[CComCachedTearOffObject::Release](#release)|递减引用计数为`CComCachedTearOffObject`对象，并销毁它，如果引用计数为 0。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::m_contained](#m_contained)|一个`CComContainedObject`对象派生自您分离式的类 (该类`contained`)。|  
  
## <a name="remarks"></a>备注  
 `CComCachedTearOffObject` 实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)分离式接口。 此类不同于`CComTearOffObject`在于`CComCachedTearOffObject`都有自己`IUnknown`、 独立于所有者对象`IUnknown`（所有者为正在为其分离式创建的对象）。 `CComCachedTearOffObject` 保留自己的引用计数在其`IUnknown`和将自身删除后其引用计数为零。 但是，如果其分开的任何查询接口，所有者对象的引用计数`IUnknown`将递增。  
  
 如果`CComCachedTearOffObject`对象实现分离式已实例化，并为同样，相同的查询分离式接口`CComCachedTearOffObject`对象将重复使用。 相反，如果分离式接口由实现`CComTearOffObject`所有者对象中，通过再次查询的另一个`CComTearOffObject`将实例化。  
  
 在所有者类必须实现`FinalRelease`并调用`Release`上的已缓存`IUnknown`为`CComCachedTearOffObject`，这将减少其引用计数。 这将导致`CComCachedTearOffObject`的`FinalRelease`调用和分离式删除。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="addref"></a>  CComCachedTearOffObject::AddRef  
 递增引用计数的`CComCachedTearOffObject`1 的对象。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是有用的诊断和测试。  
  
##  <a name="ccomcachedtearoffobject"></a>  CComCachedTearOffObject::CComCachedTearOffObject  
 构造函数。  
  
```
CComCachedTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>参数  
 *pv*  
 [in]指向`IUnknown`的`CComCachedTearOffObject`。  
  
### <a name="remarks"></a>备注  
 初始化`CComContainedObject`成员， [m_contained](#m_contained)。  
  
##  <a name="dtor"></a>  CComCachedTearOffObject:: ~ CComCachedTearOffObject  
 析构函数。  
  
```
~CComCachedTearOffObject();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源并调用[FinalRelease](#finalrelease)。  
  
##  <a name="finalconstruct"></a>  CComCachedTearOffObject::FinalConstruct  
 调用`m_contained::FinalConstruct`来创建`m_contained`，则`CComContainedObject` <  `contained`> 用于访问由您分离式的类实现的接口的对象。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。  
  
##  <a name="finalrelease"></a>  CComCachedTearOffObject::FinalRelease  
 调用`m_contained::FinalRelease`来释放`m_contained`，则`CComContainedObject` <  `contained`> 对象。  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComCachedTearOffObject::m_contained  
 一个[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)从您分离式的类派生的对象。  
  
```
CcomContainedObject <contained> m_contained;
```     
  
### <a name="parameters"></a>参数  
 *包含*  
 [in]分离式类，派生自`CComTearOffObjectBase`和希望分离式对象以支持接口。  
  
### <a name="remarks"></a>备注  
 方法`m_contained`继承用于通过缓存分开的对象的访问在您分离式的类的分离式接口`QueryInterface`， `FinalConstruct`，和`FinalRelease`。  
  
##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface  
 检索指向所请求的接口的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 *iid*  
 [in]所请求的接口的 GUID。  
  
 *ppvObject*  
 [out]通过标识的接口指针的指针*iid*，或如果找不到该接口，则为 NULL。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 如果所请求的接口是`IUnknown`，返回一个指向`CComCachedTearOffObject`的自己`IUnknown`和递增引用计数。 否则，将查询的分离式类使用的接口[InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)方法继承自`CComObjectRootEx`。  

  
##  <a name="release"></a>  CComCachedTearOffObject::Release  
 引用计数按 1 递减，引用计数为 0，如果删除`CComCachedTearOffObject`对象。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 在非调试版本中，始终返回 0。 在调试版本中返回一个值，可能是有用的诊断或测试。  
  
## <a name="see-also"></a>请参阅  
 [CComTearOffObject 类](../../atl/reference/ccomtearoffobject-class.md)   
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [类概述](../../atl/atl-class-overview.md)
