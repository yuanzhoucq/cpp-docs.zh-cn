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
ms.openlocfilehash: e34ebffc937c3e4ef1272fdf13ddcde7513d28e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497462"
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

*license*<br/>
实现以下静态函数的类:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComClassFactory2::CreateInstance](#createinstance)|创建指定 CLSID 的对象。|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|给定许可证密钥, 创建指定 CLSID 的对象。|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|检索描述类工厂的授权功能的信息。|
|[CComClassFactory2::LockServer](#lockserver)|锁定内存中的类工厂。|
|[CComClassFactory2::RequestLicKey](#requestlickey)|创建并返回许可证密钥。|

## <a name="remarks"></a>备注

`CComClassFactory2`实现[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)接口, 该接口是[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)的扩展。 `IClassFactory2`通过许可证控制对象的创建。 在许可计算机上执行的类工厂可以提供运行时许可证密钥。 此许可证密钥允许应用程序在完整的计算机许可证不存在时实例化对象。

ATL 对象通过从[CComCoClass](../../atl/reference/ccomcoclass-class.md)派生来通常获取类工厂。 此类包含宏[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), 该宏将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)声明为默认类工厂。 若要`CComClassFactory2`使用, 请在对象的类定义中指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)宏。 例如：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`, 的模板`CComClassFactory2`参数必须实现静态函数`VerifyLicenseKey`、 `GetLicenseKey`和`IsLicenseValid`。 下面是一个简单许可证类的示例:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`派生自`CComClassFactory2Base`和*许可证*。 `CComClassFactory2Base`反过来, 派生自`IClassFactory2`和。 `CComObjectRootEx< CComGlobalsThreadModel >`

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="createinstance"></a>CComClassFactory2:: CreateInstance

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

### <a name="remarks"></a>备注

要求计算机获得完全许可。 如果完整的计算机许可证不存在, 请调用[CreateInstanceLic](#createinstancelic)。

##  <a name="createinstancelic"></a>CComClassFactory2::CreateInstanceLic

类似于[CreateInstance](#createinstance), 只不过`CreateInstanceLic`需要许可证密钥。

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
中如果该对象是作为聚合的一部分创建的, 则*pUnkOuter*必须是外部未知的。 否则, *pUnkOuter*必须为 NULL。

*pUnkReserved*<br/>
中不使用。 必须为 NULL。

*riid*<br/>
中所请求的接口的 IID。 如果*pUnkOuter*为非 NULL, 则*riid*必须是`IID_IUnknown`。

*bstrKey*<br/>
中以前通过调用`RequestLicKey`获取的运行时许可证密钥。 创建对象时需要此密钥。

*ppvObject*<br/>
弄由*riid*指定的接口指针的指针。 如果对象不支持此接口, 则将*ppvObject*设置为 NULL。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

可以使用[RequestLicKey](#requestlickey)获取许可证密钥。 若要在未经授权的计算机上创建对象, 则必须调用`CreateInstanceLic`。

##  <a name="getlicinfo"></a>CComClassFactory2::GetLicInfo

使用描述类工厂的授权功能的信息填充[LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo)结构。

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>参数

*pLicInfo*<br/>
弄指向结构的`LICINFO`指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

此结构的成员指示在给定许可证密钥的情况下, 类工厂是否允许在未经授权的计算机上创建对象。 `fRuntimeKeyAvail` *FLicVerified*成员指示是否存在完整的计算机许可证。

##  <a name="lockserver"></a>  CComClassFactory2::LockServer

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

##  <a name="requestlickey"></a>CComClassFactory2::RequestLicKey

创建并返回许可证密钥, 前提`fRuntimeKeyAvail`是[LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo)结构的成员为 TRUE。

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>参数

*dwReserved*<br/>
中不使用。 必须为零。

*pbstrKey*<br/>
弄指向许可证密钥的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

若要调用[CreateInstanceLic](#createinstancelic)来在未授权的计算机上创建对象, 则需要许可证密钥。 如果`fRuntimeKeyAvail`为 FALSE, 则只能在完全许可的计算机上创建对象。

调用[GetLicInfo](#getlicinfo)检索的值`fRuntimeKeyAvail`。

## <a name="see-also"></a>请参阅

[CComClassFactoryAutoThread 类](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClassFactorySingleton 类](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[类概述](../../atl/atl-class-overview.md)
