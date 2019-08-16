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
ms.openlocfilehash: 892153e47ac4e9dd45d5dfc01b76f1ce29d23938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497455"
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

|名称|描述|
|----------|-----------------|
|[CComClassFactory::CreateInstance](#createinstance)|创建指定 CLSID 的对象。|
|[CComClassFactory::LockServer](#lockserver)|锁定内存中的类工厂。|

## <a name="remarks"></a>备注

`CComClassFactory`实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口, 该接口包含用于创建特定 CLSID 对象的方法, 以及在内存中锁定类工厂以允许更快地创建新对象。 `IClassFactory`必须为在系统注册表中注册的每个类实现, 并为其分配 CLSID。

ATL 对象通过从[CComCoClass](../../atl/reference/ccomcoclass-class.md)派生来通常获取类工厂。 此类包括声明`CComClassFactory`为默认类工厂的宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)。 若要重写此默认值, 请`DECLARE_CLASSFACTORY`在类定义中指定一个*XXX*宏。 例如, [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex)宏为类工厂使用指定的类:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

以上类定义指定`CMyClassFactory`将用作对象的默认类工厂。 `CMyClassFactory`必须从`CComClassFactory`派生并重`CreateInstance`写。

ATL 提供三个声明类工厂的宏:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)使用通过许可证控制创建的[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), 它在多个单元中创建对象。

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)使用构造单个[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象的[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)。

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="createinstance"></a>CComClassFactory:: CreateInstance

创建指定 CLSID 的对象, 并检索此对象的接口指针。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>参数

*pUnkOuter*<br/>
中如果该对象是作为聚合的一部分创建的, 则*pUnkOuter*必须是外部未知的。 否则, *pUnkOuter*必须为 NULL。

*riid*<br/>
中所请求的接口的 IID。 如果*pUnkOuter*为非 NULL, 则*riid*必须是`IID_IUnknown`。

*ppvObj*<br/>
弄指向由*riid*标识的接口指针的指针。 如果对象不支持此接口, 则将*ppvObj*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="lockserver"></a>  CComClassFactory::LockServer

分别通过调用`_Module::Lock`和`_Module::Unlock`来递增和递减模块锁计数。

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>参数

*fLock*<br/>
中如果为 TRUE, 则锁定计数递增;否则, 锁计数将减少。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`_Module`引用[CComModule](../../atl/reference/ccommodule-class.md)的全局实例或从其派生的类。

调用`LockServer`可允许客户端持有类工厂, 以便可以快速创建多个对象。

## <a name="see-also"></a>请参阅

[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[类概述](../../atl/atl-class-overview.md)
