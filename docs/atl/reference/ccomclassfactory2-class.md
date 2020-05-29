---
title: CComClassFactory2 类
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
ms.openlocfilehash: 0cb2064cfaea6317c4522ff917f3963fca2219b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321018"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 类

此类实现[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)接口。

## <a name="syntax"></a>语法

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>参数

*许可证*<br/>
实现以下静态函数的类：

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComClass 工厂2：：创建实例](#createinstance)|创建指定的 CLSID 的对象。|
|[CComClassFactory2：：创建实例](#createinstancelic)|给定许可证密钥，创建指定的 CLSID 的对象。|
|[CComClass工厂2：：获取信息](#getlicinfo)|检索描述类工厂许可功能的信息。|
|[CComClass 工厂2：：锁服务器](#lockserver)|将类工厂锁定在内存中。|
|[CComClass 工厂2：：请求键](#requestlickey)|创建并返回许可证密钥。|

## <a name="remarks"></a>备注

`CComClassFactory2`实现[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)接口，这是[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)的扩展。 `IClassFactory2`通过许可证控制对象创建。 在许可计算机上执行的类工厂可以提供运行时许可证密钥。 此许可证密钥允许应用程序在不存在完整的计算机许可证时实例化对象。

ATL 对象通常通过[CComCoClass](../../atl/reference/ccomcoclass-class.md)获得类工厂。 此类包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，它声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)为默认类工厂。 要使用`CComClassFactory2`，请在对象的类定义中指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)宏。 例如：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`的`CComClassFactory2`模板参数必须实现静态函数`VerifyLicenseKey`和`GetLicenseKey``IsLicenseValid`。 下面是一个简单的许可证类的示例：

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`派生自和`CComClassFactory2Base`*许可证*。 `CComClassFactory2Base`反过来，派生自`IClassFactory2`和`CComObjectRootEx< CComGlobalsThreadModel >`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomclassfactory2createinstance"></a><a name="createinstance"></a>CComClass 工厂2：：创建实例

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

### <a name="remarks"></a>备注

要求机器获得完全许可。 如果不存在完整的计算机许可证，请调用[Create 实例。](#createinstancelic)

## <a name="ccomclassfactory2createinstancelic"></a><a name="createinstancelic"></a>CComClassFactory2：：创建实例

与[CreateInstance](#createinstance)类似，`CreateInstanceLic`但需要许可证密钥的除外。

```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
*/,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```

### <a name="parameters"></a>参数

*pUnkOuter*<br/>
[在]如果对象是作为聚合的一部分创建的，则*pUnkOuter*必须是外部未知对象。 否则 *，pUnkOuter*必须为 NULL。

*pUnk保留*<br/>
[在]未使用。 必须为 NULL。

*riid*<br/>
[在]请求接口的 IID。 如果*pUnkOuter*是非 NULL，*则 riid*必须为`IID_IUnknown`。

*bstrKey*<br/>
[在]以前从调用`RequestLicKey`获得的运行时许可证密钥。 创建对象需要此键。

*ppvObject*<br/>
[出]指向*riid*指定的接口指针的指针。 如果对象不支持此接口，*则 ppvObject*设置为 NULL。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

您可以使用[RequestLicKey](#requestlickey)获取许可证密钥。 为了在未经许可的计算机上创建对象，必须调用`CreateInstanceLic`。

## <a name="ccomclassfactory2getlicinfo"></a><a name="getlicinfo"></a>CComClass工厂2：：获取信息

使用描述类工厂许可功能的信息填充[LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo)结构。

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>参数

*pLicInfo*<br/>
[出]指向结构的`LICINFO`指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

此`fRuntimeKeyAvail`结构的成员指示在给定许可证密钥的情况下，类工厂是否允许在未经许可的计算机上创建对象。 *fLic 验证*成员指示是否存在完整的计算机许可证。

## <a name="ccomclassfactory2lockserver"></a><a name="lockserver"></a>CComClass 工厂2：：锁服务器

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

## <a name="ccomclassfactory2requestlickey"></a><a name="requestlickey"></a>CComClass 工厂2：：请求键

创建并返回许可证密钥，前提是`fRuntimeKeyAvail`[LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo)结构的成员为 TRUE。

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>参数

*dw保留*<br/>
[在]未使用。 必须为零。

*pbstrKey*<br/>
[出]指向许可证密钥的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

调用[CreateA实例Lic](#createinstancelic)以在未许可的计算机上创建对象需要许可证密钥。 如果`fRuntimeKeyAvail`为 FALSE，则只能在完全许可的计算机上创建对象。

调用[GetLicInfo](#getlicinfo)以检索`fRuntimeKeyAvail`的值。

## <a name="see-also"></a>另请参阅

[CComclass 工厂自动线程类](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClassFactorySingleton 类](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThread模型](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[类概述](../../atl/atl-class-overview.md)
