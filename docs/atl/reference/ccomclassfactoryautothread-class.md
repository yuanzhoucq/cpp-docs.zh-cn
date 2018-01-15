---
title: "CComClassFactoryAutoThread 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
dev_langs: C++
helpviewer_keywords: CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 916bd22a982e70a7acb50793723be23416516d04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomclassfactoryautothread-class"></a>CComClassFactoryAutoThread 类
此类实现[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)接口，并允许在多个单元中创建的对象。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CComClassFactoryAutoThread 
   : public IClassFactory, 
     public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|创建指定的 CLSID 的对象。|  
|[CComClassFactoryAutoThread::LockServer](#lockserver)|锁定内存中的类工厂。|  
  
## <a name="remarks"></a>备注  
 `CComClassFactoryAutoThread`类似于[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但允许在多个单元中创建的对象。 若要利用此支持，派生从你 EXE 模块[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
 ATL 对象通常通过派生自获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 若要使用`CComClassFactoryAutoThread`，指定[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)对象的类定义中的宏。 例如:  
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 `CComClassFactoryAutoThread`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcom.h  
  
##  <a name="createinstance"></a>CComClassFactoryAutoThread::CreateInstance  
 创建指定的 CLSID 的对象并检索到此对象的接口指针。  
  
```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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
  
### <a name="remarks"></a>备注  
 如果你的模块派生自[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)，`CreateInstance`首先选择一个线程以在关联的单元中创建对象。  
  
##  <a name="lockserver"></a>CComClassFactoryAutoThread::LockServer  
 递增和递减模块锁计数通过调用**_Module::Lock**和**_Module::Unlock**分别。  
  
```
STDMETHODIMP LockServer(BOOL fLock);
```  
  
### <a name="parameters"></a>参数  
 `fLock`  
 [in]如果**TRUE**、 的锁计数递增; 否则为的锁计数会递减。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 使用时`CComClassFactoryAutoThread`， **_Module**通常是指全局实例[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
 调用`LockServer`允许客户端，以便可以快速创建多个对象保留的类工厂。  
  
## <a name="see-also"></a>请参阅  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 类](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactorySingleton 类](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [类概述](../../atl/atl-class-overview.md)
