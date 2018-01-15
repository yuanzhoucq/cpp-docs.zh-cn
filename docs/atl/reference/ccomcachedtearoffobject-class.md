---
title: "CComCachedTearOffObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 89240e913f46a3522062317da8089c3ae4bd81ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject 类
此类实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)分离式接口。  
  
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
 分离式类，派生自`CComTearOffObjectBase`，并且你希望你的拖曳对象以支持的接口。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|构造函数。|  
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::AddRef](#addref)|递增的引用计数`CComCachedTearOffObject`对象。|  
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|调用`m_contained::FinalConstruct`（拖曳类的方法）。|  
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|调用`m_contained::FinalRelease`（拖曳类的方法）。|  
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|返回一个指向`IUnknown`的`CComCachedTearOffObject`对象，或在拖曳类上请求的接口 (类`contained`)。|  
|[CComCachedTearOffObject::Release](#release)|递减引用计数为`CComCachedTearOffObject`对象，并销毁它，如果引用计数为 0。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::m_contained](#m_contained)|A`CComContainedObject`从拖曳类派生的对象 (类`contained`)。|  
  
## <a name="remarks"></a>备注  
 `CComCachedTearOffObject`实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)分离式接口。 此类不同于`CComTearOffObject`在于`CComCachedTearOffObject`都具有其自己**IUnknown**、 独立于所有者对象**IUnknown** （所有者是为其拖曳正在创建的对象）。 `CComCachedTearOffObject`保留自己的引用计数在其**IUnknown**并删除本身后的引用计数为零。 但是，如果你查询其拖曳任何接口，所有者对象的引用计数**IUnknown**将递增。  
  
 如果`CComCachedTearOffObject`对象分离式实现已实例化，并再次，对同一分离式接口`CComCachedTearOffObject`重用对象。 相反，如果分离式接口来实现`CComTearOffObject`所有者对象中，通过再次查询的另一个`CComTearOffObject`将实例化。  
  
 所有者类必须实现`FinalRelease`并调用**版本**上的已缓存**IUnknown**为`CComCachedTearOffObject`，这将减少其引用计数。 这将导致`CComCachedTearOffObject`的`FinalRelease`调用和分离式删除。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcom.h  
  
##  <a name="addref"></a>CComCachedTearOffObject::AddRef  
 引用计数递增 1 `CComCachedTearOffObject` 1 的对象。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断和测试。  
  
##  <a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject  
 构造函数。  
  
```
CComCachedTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 [in]指向**IUnknown**的`CComCachedTearOffObject`。  
  
### <a name="remarks"></a>备注  
 初始化`CComContainedObject`成员， [m_contained](#m_contained)。  
  
##  <a name="dtor"></a>CComCachedTearOffObject:: ~ CComCachedTearOffObject  
 析构函数。  
  
```
~CComCachedTearOffObject();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源和调用[FinalRelease](#finalrelease)。  
  
##  <a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct  
 调用**m_contained::FinalConstruct**创建`m_contained`、 `CComContainedObject` <  `contained`> 用于访问由你拖曳类实现的接口的对象。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease  
 调用**m_contained::FinalRelease**免费`m_contained`、 `CComContainedObject` <  `contained`> 对象。  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComCachedTearOffObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)从拖曳类派生的对象。  
  
```
CcomContainedObject <contained> m_contained;
```     
  
### <a name="parameters"></a>参数  
 `contained`  
 [in]分离式类，派生自`CComTearOffObjectBase`，并且你希望你的拖曳对象以支持的接口。  
  
### <a name="remarks"></a>备注  
 方法`m_contained`继承用于通过缓存拖曳对象的访问拖曳类中的分离式接口`QueryInterface`， `FinalConstruct`，和`FinalRelease`。  
  
##  <a name="queryinterface"></a>CComCachedTearOffObject::QueryInterface  
 检索指向所请求的接口的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]所请求接口的 GUID。  
  
 `ppvObject`  
 [out]指向由标识的接口指针的指针`iid`，或**NULL**如果找不到该接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 如果所请求的接口是**IUnknown**，返回一个指向`CComCachedTearOffObject`的自己**IUnknown**和递增引用计数。 否则，查询对于上你拖曳类使用的接口[InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)方法继承自`CComObjectRootEx`。  

  
##  <a name="release"></a>CComCachedTearOffObject::Release  
 递减引用计数 1，如果引用计数为 0，删除`CComCachedTearOffObject`对象。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 在非调试版本中，始终返回 0。 在调试版本中，返回一个值，可能是用于诊断或测试。  
  
## <a name="see-also"></a>请参阅  
 [CComTearOffObject 类](../../atl/reference/ccomtearoffobject-class.md)   
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [类概述](../../atl/atl-class-overview.md)
