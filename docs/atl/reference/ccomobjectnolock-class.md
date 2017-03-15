---
title: "CComObjectNoLock 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComObjectNoLock
- ATL::CComObjectNoLock
- ATL.CComObjectNoLock<Base>
- CComObjectNoLock
- ATL::CComObjectNoLock<Base>
dev_langs:
- C++
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 4cf4cad1a3b1a4ac0a21ef76a0eaca35732abf3a
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock 类
此类实现**IUnknown**的非聚合的对象，但不会递增模块锁计数的构造函数中。  
  
## <a name="syntax"></a>语法  
  
```
template<class Base>  
class CComObjectNoLock : public Base
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持任何其他接口也一样。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|构造函数。|  
|[CComObjectNoLock:: ~ CComObjectNoLock](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComObjectNoLock::AddRef](#addref)|递增对对象的引用计数。|  
|[CComObjectNoLock::QueryInterface](#queryinterface)|返回指向所请求的接口的指针。|  
|[CComObjectNoLock::Release](#release)|递减引用计数对象。|  
  
## <a name="remarks"></a>备注  
 `CComObjectNoLock`类似于[CComObject](../../atl/reference/ccomobject-class.md) ，因为它实现了[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)非聚合的对象; 但是，`CComObjectNoLock`构造函数中不递增模块锁计数。  
  
 ATL 使用`CComObjectNoLock`内部的类工厂。 一般情况下，您不会直接使用此类。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `CComObjectNoLock`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-nameaddrefa--ccomobjectnolockaddref"></a><a name="addref"></a>CComObjectNoLock::AddRef  
 递增对对象的引用计数。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 可能是有用的诊断或测试一个值。  
  
##  <a name="a-nameccomobjectnolocka--ccomobjectnolockccomobjectnolock"></a><a name="ccomobjectnolock"></a>CComObjectNoLock::CComObjectNoLock  
 构造函数。 与不同[CComObject](../../atl/reference/ccomobject-class.md)，不会增加模块锁计数。  
  
```
CComObjectNoLock(void* = NULL);
```  
  
### <a name="parameters"></a>参数  
 **void\***  
 [in]未使用此未命名的参数。 它位于与其他对称**CCom***XXX*`Object`*XXX*构造函数。  
  
##  <a name="a-namedtora--ccomobjectnolockccomobjectnolock"></a><a name="dtor"></a>CComObjectNoLock:: ~ CComObjectNoLock  
 析构函数。  
  
```
~CComObjectNoLock();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源并调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。  

  
##  <a name="a-namequeryinterfacea--ccomobjectnolockqueryinterface"></a><a name="queryinterface"></a>CComObjectNoLock::QueryInterface  
 检索指向所请求的接口的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]正在请求的接口的标识符。  
  
 `ppvObject`  
 [out]指向由标识的接口指针的指针`iid`。 如果该对象不支持此接口，`ppvObject`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="a-namereleasea--ccomobjectnolockrelease"></a><a name="release"></a>CComObjectNoLock::Release  
 递减引用计数对象。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 在调试版本中**版本**返回一个值，可能是有用的诊断或测试。 在非调试生成中，**版本**始终返回 0。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

