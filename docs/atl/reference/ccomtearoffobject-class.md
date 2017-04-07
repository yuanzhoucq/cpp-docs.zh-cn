---
title: "CComTearOffObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
dev_langs:
- C++
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 3e8e997f26df1adca8050bd4d967a38297685831
ms.lasthandoff: 02/24/2017

---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject 类
此类实现分离式接口。  
  
## <a name="syntax"></a>语法  
  
```
template<class Base>
class CComTearOffObject : public Base
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 您可拖曳的类，派生自`CComTearOffObjectBase`和希望拖曳对象以支持这些接口。  
  
 ATL 在两个阶段中实现它的分离式接口 —`CComTearOffObjectBase`方法处理引用计数和`QueryInterface`，尽管`CComTearOffObject`实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|构造函数。|  
|[CComTearOffObject:: ~ CComTearOffObject](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComTearOffObject::AddRef](#addref)|递增引用计数为`CComTearOffObject`对象。|  
|[CComTearOffObject::QueryInterface](#queryinterface)|返回指向所请求的接口在您分离式的类或所有者类上的指针。|  
|[CComTearOffObject::Release](#release)|递减引用计数为`CComTearOffObject`对象，并将其销毁。|  
  
### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase 方法  
  
|||  
|-|-|  
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|构造函数。|  
  
### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase 数据成员  
  
|||  
|-|-|  
|[m_pOwner](#m_powner)|一个指向`CComObject`派生自所有者类。|  
  
## <a name="remarks"></a>备注  
 `CComTearOffObject`将作为单独的对象，仅当该接口查询时实例化实现分离式接口。 拖曳时将删除其引用计数变为零。 通常情况下，您构建很少使用，因为您的主要对象的所有实例中，使用分离式节省 vtable 指针的接口的分离式接口。  
  
 应派生拖曳从实现的类`CComTearOffObjectBase`和从希望拖曳对象以支持的任何一个接口。 `CComTearOffObjectBase`在所有者类和线程模型上模板化。 所有者类是对象的为其拖曳正在实现的类。 如果不指定线程模型，则使用默认的线程模型。  
  
 为您分离式的类，应创建 COM 映射。 当分离式实例化 ATL 时，它将创建**CComTearOffObject\<CYourTearOffClass&1;>**或**CComCachedTearOffObject\<CYourTearOffClass&1;>**。  
  
 例如，在寻呼机示例中，`CBeeper2`类是分开的类和`CBeeper`类是所有者类︰  
  
 [!code-cpp[NVC_ATL_COM&#43;](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `CComTearOffObject`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="addref"></a>CComTearOffObject::AddRef  
 递增引用计数的`CComTearOffObject`由一个对象。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能会有助于诊断和测试。  
  
##  <a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject  
 构造函数。  
  
```
CComTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 [in]将转换为指向的指针的指针**CComObject\<所有者&1;>**对象。  
  
### <a name="remarks"></a>备注  
 该所有者的引用计数递增&1;。  
  
##  <a name="dtor"></a>CComTearOffObject:: ~ CComTearOffObject  
 析构函数。  
  
```
~CComTearOffObject();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源，而该模块的调用 FinalRelease，并减少锁计数。  
  
##  <a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase  
 构造函数。  
  
```
CComTearOffObjectBase();
```  
  
### <a name="remarks"></a>备注  
 初始化[m_pOwner](#m_powner)成员**NULL**。  
  
##  <a name="m_powner"></a>CComTearOffObject::m_pOwner  
 一个指向[CComObject](../../atl/reference/ccomobject-class.md)对象派生自*所有者*。  
  
```
CComObject<Owner>* m_pOwner;
```  
  
### <a name="parameters"></a>参数  
 *所有者*  
 [in]为其拖曳要实现的类。  
  
### <a name="remarks"></a>备注  
 将指针初始化为**NULL**在构造期间。  
  
##  <a name="queryinterface"></a>CComTearOffObject::QueryInterface  
 检索指向所请求的接口的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]正在请求的接口的 IID。  
  
 `ppvObject`  
 [out]指向由标识的接口指针的指针`iid`，或**NULL**如果找不到该接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 对于您分离式的类上的接口第一次查询。 如果接口不存在，所有者对象上的接口的查询。 如果所请求的接口是**IUnknown**，返回**IUnknown**的所有者。  
  
##  <a name="release"></a>CComTearOffObject::Release  
 引用计数按&1; 递减并且，如果引用计数为零时，将删除`CComTearOffObject`。  
  
```
STDMETHOD_ULONG Release();
```  
  
### <a name="return-value"></a>返回值  
 在非调试版本中，始终返回零。 在调试版本中，返回一个值，可能是有用的诊断或测试。  
  
## <a name="see-also"></a>另请参阅  
 [CComCachedTearOffObject 类](../../atl/reference/ccomcachedtearoffobject-class.md)   
 [类概述](../../atl/atl-class-overview.md)

