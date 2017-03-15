---
title: "CComObjectGlobal 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectGlobal
- ATL::CComObjectGlobal<Base>
- ATL::CComObjectGlobal
- ATL.CComObjectGlobal
- ATL.CComObjectGlobal<Base>
dev_langs:
- C++
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
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
ms.openlocfilehash: 8c371eee9de660a2bb08e67f35a5a6c81d32eee0
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal 类
此类管理上包含的模块的引用计数您`Base`对象。  
  
## <a name="syntax"></a>语法  
  
```
template<class Base>
class CComObjectGlobal : public Base
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 您的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持任何其他接口也一样。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|构造函数。|  
|[CComObjectGlobal:: ~ CComObjectGlobal](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComObjectGlobal::AddRef](#addref)|实现全局`AddRef`。|  
|[CComObjectGlobal::QueryInterface](#queryinterface)|实现全局`QueryInterface`。|  
|[CComObjectGlobal::Release](#release)|实现全局**版本**。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|包含**HRESULT**在构造过程中返回`CComObjectGlobal`对象。|  
  
## <a name="remarks"></a>备注  
 `CComObjectGlobal`管理上包含的模块的引用计数您`Base`对象。 `CComObjectGlobal`确保您的对象不会删除，只要该模块不会被释放。 在整个模块上的引用计数变为零时，将只删除您的对象。  
  
 例如，使用`CComObjectGlobal`，类工厂可以容纳一个常见的全局对象，由所有客户端共享。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `CComObjectGlobal`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-nameaddrefa--ccomobjectglobaladdref"></a><a name="addref"></a>CComObjectGlobal::AddRef  
 将该对象的引用计数加 1。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能会有助于诊断和测试。  
  
### <a name="remarks"></a>备注  
 默认情况下，`AddRef`调用**_Module::Lock**，其中**_Module**的全局实例[CComModule](../../atl/reference/ccommodule-class.md)或从其派生的类。  
  
##  <a name="a-nameccomobjectglobala--ccomobjectglobalccomobjectglobal"></a><a name="ccomobjectglobal"></a>CComObjectGlobal::CComObjectGlobal  
 构造函数。 调用`FinalConstruct`，然后设置[m_hResFinalConstruct](#m_hresfinalconstruct)到`HRESULT`返回`FinalConstruct`。  
  
```
CComObjectGlobal(void* = NULL));
```  
  
### <a name="remarks"></a>备注  
 如果您不派生基类从[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)，您必须提供您自己`FinalConstruct`方法。 析构函数调用 `FinalRelease`。  
  
##  <a name="a-namedtora--ccomobjectglobalccomobjectglobal"></a><a name="dtor"></a>CComObjectGlobal:: ~ CComObjectGlobal  
 析构函数。  
  
```
CComObjectGlobal();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源并调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。  
  
##  <a name="a-namemhresfinalconstructa--ccomobjectglobalmhresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectGlobal::m_hResFinalConstruct  
 包含`HRESULT`调用`FinalConstruct`的构造期间`CComObjectGlobal`对象。  
  
```
HRESULT m_hResFinalConstruct;
```  
  
##  <a name="a-namequeryinterfacea--ccomobjectglobalqueryinterface"></a><a name="queryinterface"></a>CComObjectGlobal::QueryInterface  
 检索指向请求的接口指针的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]正在请求的接口的 GUID。  
  
 `ppvObject`  
 [out]指向 iid，由标识的接口指针的指针或**NULL**如果找不到该接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 `QueryInterface` 仅处理 COM 映射表中的接口。  
  
##  <a name="a-namereleasea--ccomobjectglobalrelease"></a><a name="release"></a>CComObjectGlobal::Release  
 引用的对象计数按 1 递减。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 在调试版本中**版本**返回一个值，可能会有助于诊断和测试。 在非调试生成中，**版本**始终返回 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，**版本**调用**_Module::Unlock**，其中**_Module**的全局实例[CComModule](../../atl/reference/ccommodule-class.md)或从其派生的类。  
  
## <a name="see-also"></a>另请参阅  
 [CComObjectStack 类](../../atl/reference/ccomobjectstack-class.md)   
 [CComAggObject 类](../../atl/reference/ccomaggobject-class.md)   
 [CComObject 类](../../atl/reference/ccomobject-class.md)   
 [类概述](../../atl/atl-class-overview.md)

