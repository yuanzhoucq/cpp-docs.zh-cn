---
title: "CComTearOffObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 80be7d80af5a6c8fa2c47bc0e853020663f2ceae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
 分离式类，派生自`CComTearOffObjectBase`，并且你希望你的拖曳对象以支持的接口。  
  
 ATL 在两个阶段实现其分离式接口 —`CComTearOffObjectBase`方法句柄引用计数和`QueryInterface`，虽然`CComTearOffObject`实现[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|构造函数。|  
|[CComTearOffObject:: ~ CComTearOffObject](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComTearOffObject::AddRef](#addref)|递增的引用计数`CComTearOffObject`对象。|  
|[CComTearOffObject::QueryInterface](#queryinterface)|在您分离式的类或所有者类上，将指针返回到所请求的接口。|  
|[CComTearOffObject::Release](#release)|递减引用计数为`CComTearOffObject`对象，并销毁它。|  
  
### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase 方法  
  
|||  
|-|-|  
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|构造函数。|  
  
### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase 数据成员  
  
|||  
|-|-|  
|[m_pOwner](#m_powner)|指向的指针`CComObject`派生自所有者类。|  
  
## <a name="remarks"></a>备注  
 `CComTearOffObject`作为一个单独的对象，仅当该接口查询搜索时实例化实现分离式接口。 分离式就会删除其引用计数变为零。 通常情况下，你会生成很少使用的因为您的主要对象的所有实例中，使用拖曳可节省 vtable 指针的接口的分离式接口。  
  
 你应派生类实现从分离式`CComTearOffObjectBase`和从您希望拖曳对象以支持的任何接口。 `CComTearOffObjectBase`进行模板所有者类和线程模型。 所有者类是为其拖曳正在实现的对象的类。 如果未指定线程模型，则使用默认线程模型。  
  
 应为拖曳类来创建 COM 映射。 当 ATL 分离式实例化时，它将创建**CComTearOffObject\<CYourTearOffClass >**或**CComCachedTearOffObject\<CYourTearOffClass >**。  
  
 例如，在寻呼机示例中，`CBeeper2`类是拖曳类和`CBeeper`类是所有者类：  
  
 [!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Base`  
  
 `CComTearOffObject`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcom.h  
  
##  <a name="addref"></a>CComTearOffObject::AddRef  
 引用计数递增 1`CComTearOffObject`逐个的对象。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断和测试。  
  
##  <a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject  
 构造函数。  
  
```
CComTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 [in]将转换为指向的指针的指针**CComObject\<所有者 >**对象。  
  
### <a name="remarks"></a>备注  
 所有者的引用计数增加 1。  
  
##  <a name="dtor"></a>CComTearOffObject:: ~ CComTearOffObject  
 析构函数。  
  
```
~CComTearOffObject();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源时，调用 FinalRelease，并减少模块锁定计数。  
  
##  <a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase  
 构造函数。  
  
```
CComTearOffObjectBase();
```  
  
### <a name="remarks"></a>备注  
 初始化[m_pOwner](#m_powner)成员**NULL**。  
  
##  <a name="m_powner"></a>CComTearOffObject::m_pOwner  
 指向的指针[CComObject](../../atl/reference/ccomobject-class.md)对象派生自*所有者*。  
  
```
CComObject<Owner>* m_pOwner;
```  
  
### <a name="parameters"></a>参数  
 *所有者*  
 [in]为其拖曳正在实现的类。  
  
### <a name="remarks"></a>备注  
 指针初始化为**NULL**在构造期间。  
  
##  <a name="queryinterface"></a>CComTearOffObject::QueryInterface  
 检索指向所请求的接口的指针。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]所请求接口的 IID。  
  
 `ppvObject`  
 [out]指向由标识的接口指针的指针`iid`，或**NULL**如果找不到该接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 对于你拖曳类上的接口第一次查询。 如果接口不存在，所有者对象上的接口的查询。 如果所请求的接口是**IUnknown**，返回**IUnknown**的所有者。  
  
##  <a name="release"></a>CComTearOffObject::Release  
 递减引用计数 1，如果引用计数为零，删除`CComTearOffObject`。  
  
```
STDMETHOD_ULONG Release();
```  
  
### <a name="return-value"></a>返回值  
 在非调试版本中，始终返回零。 在调试版本中，返回一个值，可能是用于诊断或测试。  
  
## <a name="see-also"></a>请参阅  
 [CComCachedTearOffObject 类](../../atl/reference/ccomcachedtearoffobject-class.md)   
 [类概述](../../atl/atl-class-overview.md)
