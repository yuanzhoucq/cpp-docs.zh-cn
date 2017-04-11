---
title: "CComClassFactory 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: a0c1c115bfffa1de9a2a8c91c5268de66c68e7cd
ms.lasthandoff: 03/31/2017

---
# <a name="ccomclassfactory-class"></a>CComClassFactory 类
此类实现[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)接口。  
  
## <a name="syntax"></a>语法  
  
```
class CComClassFactory 
   : public IClassFactory,  
     public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComClassFactory::CreateInstance](#createinstance)|创建指定的 CLSID 的对象。|  
|[CComClassFactory::LockServer](#lockserver)|锁定内存中的类工厂。|  
  
## <a name="remarks"></a>备注  
 `CComClassFactory`实现[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)接口，其中包含用于创建特定的 CLSID，一个对象，以及锁定内存中要允许更快地创建新对象的类工厂方法。 **IClassFactory**必须为系统注册表中和为你分配 CLSID 注册每个类实现。  
  
 ATL 对象通常通过派生自获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中声明`CComClassFactory`作为默认类工厂。 若要重写此默认值，指定之一`DECLARE_CLASSFACTORY` *XXX*在类定义的宏。 例如， [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex)宏的类工厂使用指定的类︰  
  
 [!code-cpp[NVC_ATL_COM #8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]  
  
 上面的类定义指定**CMyClassFactory**将用作对象的默认类工厂。 **CMyClassFactory**必须派生自`CComClassFactory`，并重写`CreateInstance`。  
  
 ATL 提供了三个其他声明类工厂的宏︰  
  
- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，它可以控制通过许可证的创建。  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，这将在多个单元中创建对象。  
  
- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)使用[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，它构造单个[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="createinstance"></a>CComClassFactory::CreateInstance  
 创建指定的 CLSID 的对象并检索到此对象的接口指针。  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>参数  
 `pUnkOuter`  
 [in]如果该对象正在创建的聚合时，一部分然后`pUnkOuter`必须是未知的外部对象。 否则为`pUnkOuter`必须**NULL**。  
  
 `riid`  
 [in]所请求的接口的 IID。 如果`pUnkOuter`为非**NULL**，`riid`必须**IID_IUnknown**。  
  
 `ppvObj`  
 [out]指向由标识的接口指针的指针`riid`。 如果对象不支持此接口，`ppvObj`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="lockserver"></a>CComClassFactory::LockServer  
 递增和递减模块锁计数通过调用**_Module::Lock**和**_Module::Unlock**分别。  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>参数  
 `fLock`  
 [in]如果**TRUE**、 的锁计数递增; 否则为的锁计数会递减。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 **_Module**的全局实例是指[CComModule](../../atl/reference/ccommodule-class.md)或从它派生的类。  
  
 调用`LockServer`允许客户端，以便可以快速地创建多个对象保留的类工厂。  
  
## <a name="see-also"></a>另请参阅  
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [类概述](../../atl/atl-class-overview.md)

