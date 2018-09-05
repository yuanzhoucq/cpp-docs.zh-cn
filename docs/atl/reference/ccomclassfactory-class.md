---
title: CComClassFactory 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6bf6f830441482e17bd45c331f4281cb49312337
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765094"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory 类

此类实现[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)接口。

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
|[CComClassFactory::LockServer](#lockserver)|锁定在内存中的类工厂。|

## <a name="remarks"></a>备注

`CComClassFactory` 实现[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，它包含用于创建特定的 CLSID 的对象，以及锁定的内存，这样更快地创建新对象中的类工厂方法。 `IClassFactory` 必须为每个类都可以注册在系统注册表中并向你分配 CLSID 实现。

ATL 对象通常通过继承获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中声明`CComClassFactory`作为默认类工厂。 若要重写此默认值，指定一个`DECLARE_CLASSFACTORY` *XXX*在类定义中的宏。 例如， [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex)宏类工厂使用指定的类：

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

上面的类定义指定`CMyClassFactory`将用作对象的默认类工厂。 `CMyClassFactory` 必须派生自`CComClassFactory`并重写`CreateInstance`。

ATL 提供了三个其他声明类工厂的宏：

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，它可以控制创建通过许可证。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，用于在多个单元中创建对象。

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)使用[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，该构造一个[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象。

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="createinstance"></a>  CComClassFactory::CreateInstance

创建指定的 CLSID 的对象，并检索到此对象的接口指针。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>参数

*pUnkOuter*  
[in]如果对象正在创建的聚合，然后*pUnkOuter*必须是未知的外部。 否则为*pUnkOuter*必须为 NULL。

*riid*  
[in]所请求的接口的 IID。 如果*pUnkOuter*为非 NULL *riid*必须是`IID_IUnknown`。

*ppvObj*  
[out]通过标识的接口指针的指针*riid*。 如果该对象不支持此接口， *ppvObj*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="lockserver"></a>  CComClassFactory::LockServer

递增和递减模块锁计数通过调用`_Module::Lock`和`_Module::Unlock`分别。

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>参数

*纷纷采用*  
[in]如果为 TRUE，将增加的锁计数;否则，将减少锁计数。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`_Module` 全局实例是指[CComModule](../../atl/reference/ccommodule-class.md)或从其派生的类。

调用`LockServer`允许客户端，以便可以快速创建多个对象保存到一个类工厂。

## <a name="see-also"></a>请参阅

[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
[类概述](../../atl/atl-class-overview.md)
