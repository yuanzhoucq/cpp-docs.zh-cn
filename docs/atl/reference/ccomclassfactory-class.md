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
- ATL.CComClassFactory
- CComClassFactory
- ATL::CComClassFactory
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c7c488732d7b32248acaaa5c5c9c6a29404c3872
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CComClassFactory::CreateInstance](#createinstance)|创建指定的 CLSID 的对象。|  
|[CComClassFactory::LockServer](#lockserver)|锁定在内存中的类工厂。|  
  
## <a name="remarks"></a>备注  
 `CComClassFactory`实现[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)接口，它包含用于创建特定的 CLSID，一个对象，以及锁定在内存中允许更快地创建新对象的类工厂的方法。 **IClassFactory**必须为您注册系统注册表中以及为你分配 CLSID 的每个类实现。  
  
 ATL 对象通常通过派生自获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](http://msdn.microsoft.com/library/51a6b925-07c0-4d3a-9174-0b8c808975e4)，其中声明`CComClassFactory`作为默认类工厂。 若要重写此默认值，指定一个`DECLARE_CLASSFACTORY` *XXX*在类定义的宏。 例如， [DECLARE_CLASSFACTORY_EX](http://msdn.microsoft.com/library/4181ef00-0f30-4e19-b0ee-e7648062e926)宏的类工厂使用指定的类︰  
  
 [!code-cpp[NVC_ATL_COM&#8;](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]  
  
 上面的类定义指定**CMyClassFactory**将用作该对象的默认类工厂。 **CMyClassFactory**必须派生自`CComClassFactory`并重写`CreateInstance`。  
  
 ATL 提供三个其他声明类工厂的宏︰  
  
- [DECLARE_CLASSFACTORY2](http://msdn.microsoft.com/library/38a6c969-7297-4bb1-9ba6-1fe2d355b285)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，哪些控件创建到一个许可证。  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](http://msdn.microsoft.com/library/19d7105e-03e8-4412-9f5e-5384c8a5e18f)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，从而在多个单元中创建对象。  
  
- [DECLARE_CLASSFACTORY_SINGLETON](http://msdn.microsoft.com/library/0e4a3964-c03d-463e-884c-fe3b416db478)使用[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，它会构造一个[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-namecreateinstancea--ccomclassfactorycreateinstance"></a><a name="createinstance"></a>CComClassFactory::CreateInstance  
 创建指定的 CLSID 的对象，并检索到此对象的接口指针。  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>参数  
 `pUnkOuter`  
 [in]如果该对象被作为的一部分创建聚合时，然后`pUnkOuter`必须是未知的外部对象。 否则为`pUnkOuter`必须**NULL**。  
  
 `riid`  
 [in]所请求的接口的 IID。 如果`pUnkOuter`为非**NULL**，`riid`必须**IID_IUnknown**。  
  
 `ppvObj`  
 [out]指向由标识的接口指针的指针`riid`。 如果该对象不支持此接口，`ppvObj`设置为**NULL**。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="a-namelockservera--ccomclassfactorylockserver"></a><a name="lockserver"></a>CComClassFactory::LockServer  
 递增和递减模块锁计数通过调用**_Module::Lock**和**_Module::Unlock**分别。  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>参数  
 `fLock`  
 [in]如果**TRUE**、 锁计数递增; 否则为锁计数会递减。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 **_Module**的全局实例是指[CComModule](../../atl/reference/ccommodule-class.md)或从其派生的类。  
  
 调用`LockServer`允许客户端，以便可以快速创建多个对象保存到类工厂。  
  
## <a name="see-also"></a>另请参阅  
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [类概述](../../atl/atl-class-overview.md)

