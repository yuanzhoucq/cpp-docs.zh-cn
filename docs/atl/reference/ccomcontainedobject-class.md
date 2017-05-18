---
title: "CComContainedObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: ac817cedb4c7ed67e698969b14645f5659aab2ad
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="ccomcontainedobject-class"></a>CComContainedObject 类
此类实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)通过委派给所有者对象的**IUnknown**。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class Base>  
class CComContainedObject : public Base
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 你的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|构造函数。 初始化所有者对象的成员指针`IUnknown`。|  
|[CComContainedObject:: ~ CComContainedObject](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComContainedObject::AddRef](#addref)|递增所有者对象上的引用计数。|  
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|检索所有者对象`IUnknown`。|  
|[CComContainedObject::QueryInterface](#queryinterface)|检索指向所有者对象上请求的接口的指针。|  
|[CComContainedObject::Release](#release)|递减引用计数所有者对象上。|  
  
## <a name="remarks"></a>备注  
 使用 ATL`CComContainedObject`类中[CComAggObject](../../atl/reference/ccomaggobject-class.md)， [CComPolyObject](../../atl/reference/ccompolyobject-class.md)，和[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)。 `CComContainedObject`实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)通过委派给所有者对象的**IUnknown**。 （所有者是聚合，在外部对象或为其创建分离式接口的对象）。`CComContainedObject`调用`CComObjectRootEx`的`OuterQueryInterface`， `OuterAddRef`，和`OuterRelease`、 通过所有继承`Base`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `CComContainedObject`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="addref"></a>CComContainedObject::AddRef  
 递增所有者对象上的引用计数。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断或测试。  
  
##  <a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject  
 构造函数。  
  
```
CComContainedObject(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 [in]所有者对象**IUnknown**。  
  
### <a name="remarks"></a>备注  
 集`m_pOuterUnknown`成员指针 (通过继承`Base`类) 到`pv`。  
  
##  <a name="dtor"></a>CComContainedObject:: ~ CComContainedObject  
 析构函数。  
  
```
~CComContainedObject();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown  
 返回`m_pOuterUnknown`成员指针 (通过继承*基*类)，用于保存所有者对象**IUnknown**。  
  
```
IUnknown* GetControllingUnknown();
```  
  
### <a name="return-value"></a>返回值  
 所有者对象**IUnknown**。  
  
### <a name="remarks"></a>备注  
 此方法可能是虚拟如果`Base`已声明[DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown)宏。  
  
##  <a name="queryinterface"></a>CComContainedObject::QueryInterface  
 检索指向所有者对象上请求的接口的指针。  
  
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
  
##  <a name="release"></a>CComContainedObject::Release  
 递减引用计数所有者对象上。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 在调试版本中，**版本**返回一个值，可能是用于诊断或测试。 在非调试版本中，**版本**始终返回 0。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

