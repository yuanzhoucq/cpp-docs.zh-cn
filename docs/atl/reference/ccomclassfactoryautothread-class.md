---
title: CComClassFactoryAutoThread 类
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: 73879a73a48290e19d2a27307884953129826df7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497490"
---
# <a name="ccomclassfactoryautothread-class"></a>CComClassFactoryAutoThread 类

此类实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，并允许在多个单元中创建对象。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

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
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|创建指定 CLSID 的对象。|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|锁定内存中的类工厂。|

## <a name="remarks"></a>备注

`CComClassFactoryAutoThread`类似于[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但允许在多个单元中创建对象。 若要利用此支持，请从[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)派生 EXE 模块。

ATL 对象通过从[CComCoClass](../../atl/reference/ccomcoclass-class.md)派生来通常获取类工厂。 此类包含宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，该宏将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)声明为默认类工厂。 若要`CComClassFactoryAutoThread`使用，请在对象的类定义中指定[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)宏。 例如:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="createinstance"></a>CComClassFactoryAutoThread：： CreateInstance

创建指定 CLSID 的对象，并检索此对象的接口指针。

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>参数

*pUnkOuter*<br/>
中如果该对象是作为聚合的一部分创建的，则*pUnkOuter*必须是外部未知的。 否则， *pUnkOuter*必须为 NULL。

*riid*<br/>
中所请求的接口的 IID。 如果*pUnkOuter*为非 NULL，则*riid*必须是`IID_IUnknown`。

*ppvObj*<br/>
弄指向由*riid*标识的接口指针的指针。 如果对象不支持此接口，则将*ppvObj*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果你的模块是从 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) 派生的，则`CreateInstance`首先选择一个线程以在关联单元中创建对象。

##  <a name="lockserver"></a>CComClassFactoryAutoThread：： LockServer

分别通过调用`_Module::Lock`和`_Module::Unlock`来递增和递减模块锁计数。

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>参数

*fLock*<br/>
中如果为 TRUE，则锁定计数递增;否则，锁计数将减少。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

使用`CComClassFactoryAutoThread`时， `_Module`通常是指[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)的全局实例。

调用`LockServer`可允许客户端持有类工厂，以便可以快速创建多个对象。

## <a name="see-also"></a>请参阅

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 类](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactorySingleton 类](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[类概述](../../atl/atl-class-overview.md)
