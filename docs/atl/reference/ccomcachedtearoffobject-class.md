---
title: "CComCachedTearOffObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
caps.latest.revision: 19
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 96f040c732c5545a9b8febb32fcb1636f0fe4a40
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

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
 您可拖曳的类，派生自`CComTearOffObjectBase`和希望拖曳对象以支持这些接口。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|构造函数。|  
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComCachedTearOffObject::AddRef](#addref)|递增引用计数为`CComCachedTearOffObject`对象。|  
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|调用`m_contained::FinalConstruct`（拖曳类的方法）。|  
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|调用`m_contained::FinalRelease`（拖曳类的方法）。|  
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|返回一个指向`IUnknown`的`CComCachedTearOffObject`对象，或对请求的接口上分开的类 (该类`contained`)。|  
|[CComCachedTearOffObject::Release](#release)|递减引用计数为`CComCachedTearOffObject`对象，并将其销毁，如果引用计数为 0。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CComCachedTearOffObject::m_contained](#m_contained)|一个`CComContainedObject`对象派生自您分离式的类 (该类`contained`)。|  
  
## <a name="remarks"></a>备注  
 `CComCachedTearOffObject`实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)分离式接口。 此类不同于`CComTearOffObject`在于`CComCachedTearOffObject`都具有其自己**IUnknown**、 独立于所有者对象**IUnknown** （所有者是该分离式正在为创建的对象）。 `CComCachedTearOffObject`保留自己的引用计数在其**IUnknown**和将自身删除后的引用计数为零。 但是，如果您查询其分开的任何接口，所有者对象的引用计数**IUnknown**将递增。  
  
 如果`CComCachedTearOffObject`对象实现分离式已实例化，并再次重申，同一查询分离式接口`CComCachedTearOffObject`重用对象。 与之相反，如果分离式接口实现`CComTearOffObject`再次通过所有者对象查询的另一个`CComTearOffObject`将实例化。  
  
 所有者类必须实现`FinalRelease`并调用**版本**上的已缓存**IUnknown**为`CComCachedTearOffObject`，这将减少其引用计数。 这将导致`CComCachedTearOffObject`的`FinalRelease`调用和分离式删除。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="addref"></a>CComCachedTearOffObject::AddRef  
 递增引用计数的`CComCachedTearOffObject`1 的对象。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能会有助于诊断和测试。  
  
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
 释放所有已分配的资源并调用[FinalRelease](#finalrelease)。  
  
##  <a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct  
 调用**m_contained::FinalConstruct**创建`m_contained`、 `CComContainedObject` <  `contained`1> 用于访问由您分离式的类实现的接口的对象。  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease  
 调用**m_contained::FinalRelease**以释放`m_contained`、 `CComContainedObject` <  `contained`1> 对象。  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComCachedTearOffObject::m_contained  
 一个[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)从您分离式的类派生的对象。  
  
```
CcomContainedObject <contained> m_contained;
```     
  
### <a name="parameters"></a>参数  
 `contained`  
 [in]您可拖曳的类，派生自`CComTearOffObjectBase`和希望拖曳对象以支持这些接口。  
  
### <a name="remarks"></a>备注  
 这些方法`m_contained`继承用于通过缓存分开的对象的访问拖曳类中的分离式接口`QueryInterface`， `FinalConstruct`，和`FinalRelease`。  
  
##  <a name="queryinterface"></a>CComCachedTearOffObject::QueryInterface  
 检索指向所请求的接口的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]正在请求的接口的 GUID。  
  
 `ppvObject`  
 [out]指向由标识的接口指针的指针`iid`，或**NULL**如果找不到该接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 如果所请求的接口是**IUnknown**，返回一个指向`CComCachedTearOffObject`的自己**IUnknown**和递增引用计数。 否则，对于上分开的类使用的接口会询问[InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)方法继承自`CComObjectRootEx`。  

  
##  <a name="release"></a>CComCachedTearOffObject::Release  
 递减引用计数按 1，如果引用计数为 0，删除`CComCachedTearOffObject`对象。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 在非调试版本中，始终返回 0。 在调试版本中，返回一个值，可能是有用的诊断或测试。  
  
## <a name="see-also"></a>另请参阅  
 [CComTearOffObject 类](../../atl/reference/ccomtearoffobject-class.md)   
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [类概述](../../atl/atl-class-overview.md)

