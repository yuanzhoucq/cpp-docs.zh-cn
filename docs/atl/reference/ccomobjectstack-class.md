---
title: CComObjectStack 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ac37ac5abc193082aaccb8d5de1a4f75f8a3f7c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ccomobjectstack-class"></a>CComObjectStack 类
此类创建一个临时的 COM 对象，并为其提供的主干实现**IUnknown**。  
  
## <a name="syntax"></a>语法  
  
```
template <class  Base>  
class CComObjectStack
 : public Base
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 你的类，派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如你想要的对象上支持很好地从任何其他接口。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|构造函数。|  
|[CComObjectStack:: ~ CComObjectStack](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComObjectStack::AddRef](#addref)|返回零。 在调试模式下，调用`_ASSERTE`。|  
|[CComObjectStack::QueryInterface](#queryinterface)|返回**E_NOINTERFACE**。 在调试模式下，调用`_ASSERTE`。|  
|[CComObjectStack::Release](#release)|返回零。 在调试模式下，调用`_ASSERTE`。 ~|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|包含**HRESULT**构造过程返回`CComObjectStack`对象。|  
  
## <a name="remarks"></a>备注  
 `CComObjectStack` 用于创建一个临时的 COM 对象，并提供对象的主干实现**IUnknown**。 通常情况下，该对象用作一个函数 （即，推送到堆栈） 内的局部变量。 由于该函数完成时，对象被销毁，引用计数不执行来提高工作效率。  
  
 下面的示例演示如何创建在函数内使用的 COM 对象：  
  
 [!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]  
  
 临时对象`Tempobj`推送到堆栈，并且该函数完成时自动会消失。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `CComObjectStack`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="addref"></a>  CComObjectStack::AddRef  
 返回零。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 返回零。  
  
### <a name="remarks"></a>备注  
 在调试模式下，调用`_ASSERTE`。  
  
##  <a name="ccomobjectstack"></a>  CComObjectStack::CComObjectStack  
 构造函数。  
  
```
CComObjectStack(void* = NULL);
```  
  
### <a name="remarks"></a>备注  
 调用`FinalConstruct`，然后将设置[m_hResFinalConstruct](#m_hresfinalconstruct)到`HRESULT`返回`FinalConstruct`。 如果你不派生基类从[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)，则必须提供你自己`FinalConstruct`方法。 析构函数调用 `FinalRelease`。  
  
##  <a name="dtor"></a>  CComObjectStack:: ~ CComObjectStack  
 析构函数。  
  
```
CComObjectStack();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源和调用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。  
  
##  <a name="m_hresfinalconstruct"></a>  CComObjectStack::m_hResFinalConstruct  
 包含`HRESULT`从调用返回`FinalConstruct`的构造期间`CComObjectStack`对象。  
  
```
HRESULT    m_hResFinalConstruct;
```  
  
##  <a name="queryinterface"></a>  CComObjectStack::QueryInterface  
 返回**E_NOINTERFACE**。  
  
```
HRESULT    QueryInterface(REFIID, void**)
 ;
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOINTERFACE**。  
  
### <a name="remarks"></a>备注  
 在调试模式下，调用`_ASSERTE`。  
  
##  <a name="release"></a>  CComObjectStack::Release  
 返回零。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>返回值  
 返回零。  
  
### <a name="remarks"></a>备注  
 在调试模式下，调用`_ASSERTE`。  
  
## <a name="see-also"></a>请参阅  
 [CComAggObject 类](../../atl/reference/ccomaggobject-class.md)   
 [CComObject 类](../../atl/reference/ccomobject-class.md)   
 [CComObjectGlobal 类](../../atl/reference/ccomobjectglobal-class.md)   
 [类概述](../../atl/atl-class-overview.md)
