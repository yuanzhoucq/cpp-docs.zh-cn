---
title: "CComObjectGlobal 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
dev_langs: C++
helpviewer_keywords: CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d5264a2ab8e1bbc4c3f4eac4d83d096d91e8846
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal 类
此类管理上包含的模块的引用计数你`Base`对象。  
  
## <a name="syntax"></a>语法  
  
```
template<class Base>
class CComObjectGlobal : public Base
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 你的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持很好地从任何其他接口。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
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
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|包含**HRESULT**构造过程返回`CComObjectGlobal`对象。|  
  
## <a name="remarks"></a>备注  
 `CComObjectGlobal`管理上包含的模块的引用计数你`Base`对象。 `CComObjectGlobal`确保你的对象将不会删除，只要该模块不会被释放。 在整个模块上的引用计数变为零时，仅将删除你的对象。  
  
 例如，使用`CComObjectGlobal`，类工厂可以保留一个公共的全局对象所共享的所有客户端。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `CComObjectGlobal`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcom.h  
  
##  <a name="addref"></a>CComObjectGlobal::AddRef  
 对象的引用计数递增 1。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断和测试。  
  
### <a name="remarks"></a>备注  
 默认情况下，`AddRef`调用**_Module::Lock**，其中**_Module**是全局实例[CComModule](../../atl/reference/ccommodule-class.md)或从它派生的类。  
  
##  <a name="ccomobjectglobal"></a>CComObjectGlobal::CComObjectGlobal  
 构造函数。 调用`FinalConstruct`，然后将设置[m_hResFinalConstruct](#m_hresfinalconstruct)到`HRESULT`返回`FinalConstruct`。  
  
```
CComObjectGlobal(void* = NULL));
```  
  
### <a name="remarks"></a>备注  
 如果你不派生基类从[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)，则必须提供你自己`FinalConstruct`方法。 析构函数调用 `FinalRelease`。  
  
##  <a name="dtor"></a>CComObjectGlobal:: ~ CComObjectGlobal  
 析构函数。  
  
```
CComObjectGlobal();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源和调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。  
  
##  <a name="m_hresfinalconstruct"></a>CComObjectGlobal::m_hResFinalConstruct  
 包含`HRESULT`调用`FinalConstruct`的构造期间`CComObjectGlobal`对象。  
  
```
HRESULT m_hResFinalConstruct;
```  
  
##  <a name="queryinterface"></a>CComObjectGlobal::QueryInterface  
 检索指向请求的接口指针的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]所请求接口的 GUID。  
  
 `ppvObject`  
 [out]指向 iid，由标识的接口指针的指针或**NULL**如果找不到该接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 `QueryInterface` 仅处理 COM 映射表中的接口。  
  
##  <a name="release"></a>CComObjectGlobal::Release  
 递减的引用对象的计数加 1。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 在调试版本中，**版本**返回一个值，可能是用于诊断和测试。 在非调试版本中，**版本**始终返回 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，**版本**调用**_Module::Unlock**，其中**_Module**是全局实例[CComModule](../../atl/reference/ccommodule-class.md)或从它派生的类。  
  
## <a name="see-also"></a>请参阅  
 [CComObjectStack 类](../../atl/reference/ccomobjectstack-class.md)   
 [CComAggObject 类](../../atl/reference/ccomaggobject-class.md)   
 [CComObject 类](../../atl/reference/ccomobject-class.md)   
 [类概述](../../atl/atl-class-overview.md)
