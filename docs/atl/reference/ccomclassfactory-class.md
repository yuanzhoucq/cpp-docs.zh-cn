---
title: CComClassFactory 类
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 041575339906b83488697f1db5a7f8b08b53070e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321025"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory 类

此类实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口。

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
|[CComClass 工厂：创建实例](#createinstance)|创建指定的 CLSID 的对象。|
|[CComClass 工厂：：锁服务器](#lockserver)|将类工厂锁定在内存中。|

## <a name="remarks"></a>备注

`CComClassFactory`实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，其中包含用于创建特定 CLSID 对象的方法，以及将类工厂锁定在内存中，以便更快地创建新对象。 `IClassFactory`必须针对在系统注册表中注册并为其分配 CLSID 的每个类实现。

ATL 对象通常通过[CComCoClass](../../atl/reference/ccomcoclass-class.md)获得类工厂。 此类包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，它`CComClassFactory`声明为默认类工厂。 要重写此默认值，请在类定义中`DECLARE_CLASSFACTORY`指定*XXX*宏之一。 例如[，DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex)宏对类工厂使用指定的类：

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

上面的类定义指定`CMyClassFactory`将用作对象的默认类工厂。 `CMyClassFactory`必须派生并`CComClassFactory`覆盖`CreateInstance`。

ATL 提供了声明类工厂的其他三个宏：

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，它控制通过许可证创建的。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，它可在多个单元中创建对象。

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)使用[CComClassFactory 单一项](../../atl/reference/ccomclassfactorysingleton-class.md)，它构造单个[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象。

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomclassfactorycreateinstance"></a><a name="createinstance"></a>CComClass 工厂：创建实例

创建指定的 CLSID 的对象并检索指向此对象的接口指针。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>参数

*pUnkOuter*<br/>
[在]如果对象是作为聚合的一部分创建的，则*pUnkOuter*必须是外部未知对象。 否则 *，pUnkOuter*必须为 NULL。

*riid*<br/>
[在]请求接口的 IID。 如果*pUnkOuter*是非 NULL，*则 riid*必须为`IID_IUnknown`。

*普夫奥比*<br/>
[出]指向*riid*标识的接口指针的指针。 如果对象不支持此接口，*则 ppvObj*设置为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ccomclassfactorylockserver"></a><a name="lockserver"></a>CComClass 工厂：：锁服务器

增量和递减模块锁计数分别通过调用`_Module::Lock`和`_Module::Unlock`。

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>参数

*羊群*<br/>
[在]如果为 TRUE，则锁计数将递增;如果为 TRUE，则锁定计数将递增。否则，锁计数将递减。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

`_Module`指[CComModule](../../atl/reference/ccommodule-class.md)的全局实例或从它派生的类。

调用`LockServer`允许客户端保留类工厂，以便可以快速创建多个对象。

## <a name="see-also"></a>另请参阅

[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThread模型](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[类概述](../../atl/atl-class-overview.md)
