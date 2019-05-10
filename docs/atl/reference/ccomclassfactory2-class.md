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
ms.openlocfilehash: b3b14fa59765aa72a1142e0eef41aa84abea35de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259685"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 类

此类实现[IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)接口。

## <a name="syntax"></a>语法

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>参数

*license*<br/>
实现以下静态函数的类：

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComClassFactory2::CreateInstance](#createinstance)|创建指定的 CLSID 的对象。|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|给定的许可证密钥，将创建指定的 CLSID 的对象。|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|检索描述类工厂的授权功能的信息。|
|[CComClassFactory2::LockServer](#lockserver)|锁定在内存中的类工厂。|
|[CComClassFactory2::RequestLicKey](#requestlickey)|创建并返回许可证密钥。|

## <a name="remarks"></a>备注

`CComClassFactory2` 实现[IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)接口，这是扩展的[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)。 `IClassFactory2` 控件通过许可证创建的对象。 已授权的计算机上类工厂执行可以提供运行时许可证密钥。 此许可证密钥允许应用程序的完整计算机许可证不存在时实例化对象。

ATL 对象通常通过继承获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 若要使用`CComClassFactory2`，指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)对象的类定义中的宏。 例如：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`模板参数`CComClassFactory2`，必须实现的静态函数`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。 下面是简单的许可证类的一个示例：

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2` 从这两个派生`CComClassFactory2Base`并*许可证*。 `CComClassFactory2Base`反过来，派生`IClassFactory2`和`CComObjectRootEx< CComGlobalsThreadModel >`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="createinstance"></a>  CComClassFactory2::CreateInstance

创建指定的 CLSID 的对象，并检索到此对象的接口指针。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>参数

*pUnkOuter*<br/>
[in]如果对象正在创建的聚合，然后*pUnkOuter*必须是未知的外部。 否则为*pUnkOuter*必须为 NULL。

*riid*<br/>
[in]所请求的接口的 IID。 如果*pUnkOuter*为非 NULL *riid*必须是`IID_IUnknown`。

*ppvObj*<br/>
[out]通过标识的接口指针的指针*riid*。 如果该对象不支持此接口， *ppvObj*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

要求计算机进行完全授权。 如果完整的计算机许可证不存在，则调用[CreateInstanceLic](#createinstancelic)。

##  <a name="createinstancelic"></a>  CComClassFactory2::CreateInstanceLic

类似于[CreateInstance](#createinstance)，只不过`CreateInstanceLic`需要许可证密钥。

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
[in]如果对象正在创建的聚合，然后*pUnkOuter*必须是未知的外部。 否则为*pUnkOuter*必须为 NULL。

*pUnkReserved*<br/>
[in]不使用。 必须为 NULL。

*riid*<br/>
[in]所请求的接口的 IID。 如果*pUnkOuter*为非 NULL *riid*必须是`IID_IUnknown`。

*bstrKey*<br/>
[in]通过调用以前获取的运行时许可证密钥`RequestLicKey`。 创建该对象需要此密钥。

*ppvObject*<br/>
[out]指向由指定的接口指针的指针*riid*。 如果该对象不支持此接口， *ppvObject*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

你可以获取许可证密钥 using [RequestLicKey](#requestlickey)。 若要在未授权的计算机上创建一个对象，必须调用`CreateInstanceLic`。

##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo

填充[LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo)结构描述的类工厂的信息的许可功能。

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>参数

*pLicInfo*<br/>
[out]指向`LICINFO`结构。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`fRuntimeKeyAvail`此结构的成员指示是否，提供许可证密钥，类工厂允许未经授权的计算机上创建的对象。 *FLicVerified*成员指示完整机许可证是否存在。

##  <a name="lockserver"></a>  CComClassFactory2::LockServer

递增和递减模块锁计数通过调用`_Module::Lock`和`_Module::Unlock`分别。

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>参数

*fLock*<br/>
[in]如果为 TRUE，将增加的锁计数;否则，将减少锁计数。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`_Module` 全局实例是指[CComModule](../../atl/reference/ccommodule-class.md)或从其派生的类。

调用`LockServer`允许客户端，以便可以快速创建多个对象保存到一个类工厂。

##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey

创建并返回提供的许可证密钥`fRuntimeKeyAvail`的成员[LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo)结构为 TRUE。

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>参数

*dwReserved*<br/>
[in]不使用。 必须为零。

*pbstrKey*<br/>
[out]指向指针的许可证密钥。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

许可证密钥才可进行调用[CreateInstanceLic](#createinstancelic)未授权的计算机上创建对象。 如果`fRuntimeKeyAvail`为 FALSE，则仅在完全许可的计算机上创建对象。

调用[GetLicInfo](#getlicinfo)若要检索的值`fRuntimeKeyAvail`。

## <a name="see-also"></a>请参阅

[CComClassFactoryAutoThread 类](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClassFactorySingleton 类](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[类概述](../../atl/atl-class-overview.md)
