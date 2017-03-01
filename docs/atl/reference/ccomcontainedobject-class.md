---
title: "CComContainedObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComContainedObject
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 60958f328d78205c3432f35ed4e3e3c4b652ebfe
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcontainedobject-class"></a>CComContainedObject 类
此类实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)通过将委派给所有者对象**IUnknown**。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template<class Base>  
class CComContainedObject : public Base
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|构造函数。 所有者对象的成员的指针进行初始化`IUnknown`。|  
|[CComContainedObject:: ~ CComContainedObject](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComContainedObject::AddRef](#addref)|递增所有者对象上的引用计数。|  
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|检索所有者对象`IUnknown`。|  
|[CComContainedObject::QueryInterface](#queryinterface)|检索指向所有者对象上请求的接口指针。|  
|[CComContainedObject::Release](#release)|递减引用计数在所有者对象。|  
  
## <a name="remarks"></a>备注  
 ATL 使用`CComContainedObject`类中[CComAggObject](../../atl/reference/ccomaggobject-class.md)， [CComPolyObject](../../atl/reference/ccompolyobject-class.md)，和[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)。 `CComContainedObject`实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)通过将委派给所有者对象**IUnknown**。 （所有者是聚合中的外部对象或为其创建分离式接口的对象）。`CComContainedObject`调用`CComObjectRootEx`的`OuterQueryInterface`， `OuterAddRef`，和`OuterRelease`、 通过所有继承`Base`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `CComContainedObject`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-nameaddrefa--ccomcontainedobjectaddref"></a><a name="addref"></a>CComContainedObject::AddRef  
 递增所有者对象上的引用计数。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 可能是有用的诊断或测试一个值。  
  
##  <a name="a-nameccomcontainedobjecta--ccomcontainedobjectccomcontainedobject"></a><a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject  
 构造函数。  
  
```
CComContainedObject(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 [in]所有者对象**IUnknown**。  
  
### <a name="remarks"></a>备注  
 集`m_pOuterUnknown`成员指针 (通过继承`Base`类) 到`pv`。  
  
##  <a name="a-namedtora--ccomcontainedobjectccomcontainedobject"></a><a name="dtor"></a>CComContainedObject:: ~ CComContainedObject  
 析构函数。  
  
```
~CComContainedObject();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="a-namegetcontrollingunknowna--ccomcontainedobjectgetcontrollingunknown"></a><a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown  
 返回`m_pOuterUnknown`成员指针 (通过继承*基本*类)，它持有所有者对象**IUnknown**。  
  
```
IUnknown* GetControllingUnknown();
```  
  
### <a name="return-value"></a>返回值  
 所有者对象**IUnknown**。  
  
### <a name="remarks"></a>备注  
 可以是虚拟机此方法如果`Base`已声明[DECLARE_GET_CONTROLLING_UNKNOWN](http://msdn.microsoft.com/library/82b0199a-a9d5-4f95-a711-fa1ae18e1f77)宏。  
  
##  <a name="a-namequeryinterfacea--ccomcontainedobjectqueryinterface"></a><a name="queryinterface"></a>CComContainedObject::QueryInterface  
 检索指向所有者对象上请求的接口指针。  
  
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
  
##  <a name="a-namereleasea--ccomcontainedobjectrelease"></a><a name="release"></a>CComContainedObject::Release  
 递减引用计数在所有者对象。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 在调试版本中**版本**返回一个值，可能是有用的诊断或测试。 在非调试生成中，**版本**始终返回 0。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

