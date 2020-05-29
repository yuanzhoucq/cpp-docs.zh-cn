---
title: CComclass 工厂自动线程类
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: e997d92adfa9df46c82dacbd297db495b037c6e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320908"
---
# <a name="ccomclassfactoryautothread-class"></a>CComclass 工厂自动线程类

此类实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，并允许在多个单元中创建对象。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CComClassFactoryAutoThread
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComClass 工厂自动线程：：创建实例](#createinstance)|创建指定的 CLSID 的对象。|
|[CComclass 工厂自动线程：：锁定服务器](#lockserver)|将类工厂锁定在内存中。|

## <a name="remarks"></a>备注

`CComClassFactoryAutoThread`类似于[CComClassFactory，](../../atl/reference/ccomclassfactory-class.md)但允许在多个公寓中创建对象。 要利用此支持，请从[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)派生 EXE 模块。

ATL 对象通常通过[CComCoClass](../../atl/reference/ccomcoclass-class.md)获得类工厂。 此类包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，它声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)为默认类工厂。 要使用`CComClassFactoryAutoThread`，请在对象的类定义中指定[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)宏。 例如：

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomclassfactoryautothreadcreateinstance"></a><a name="createinstance"></a>CComClass 工厂自动线程：：创建实例

创建指定的 CLSID 的对象并检索指向此对象的接口指针。

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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

### <a name="remarks"></a>备注

如果模块派生自[CComAutoThreadModule，](../../atl/reference/ccomautothreadmodule-class.md)`CreateInstance`则首先选择一个线程在关联的单元中创建对象。

## <a name="ccomclassfactoryautothreadlockserver"></a><a name="lockserver"></a>CComclass 工厂自动线程：：锁定服务器

增量和递减模块锁计数分别通过调用`_Module::Lock`和`_Module::Unlock`。

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>参数

*羊群*<br/>
[在]如果为 TRUE，则锁计数将递增;如果为 TRUE，则锁定计数将递增。否则，锁计数将递减。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

使用`CComClassFactoryAutoThread`时`_Module`，通常引用[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)的全局实例。

调用`LockServer`允许客户端保留类工厂，以便可以快速创建多个对象。

## <a name="see-also"></a>另请参阅

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 类](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactorySingleton 类](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThread模型](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[类概述](../../atl/atl-class-overview.md)
