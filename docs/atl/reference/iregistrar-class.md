---
title: IRegistrar 接口
ms.date: 2/1/2017
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
ms.openlocfilehash: 3494920164ed3a62713298d2cafdbdc27dbb2b97
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534766"
---
# <a name="iregistrar-interface"></a>IRegistrar 接口

此接口 atliface.h 中定义，供内部使用 CAtlModule 成员函数如[UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)。

## <a name="syntax"></a>语法

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>备注

请参阅主题[使用可替换参数 （注册机构的预处理器）](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)的更多详细信息。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|注册资源。 |
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| 注销该资源。|
|[IRegistrar::FileRegister](#fileregister)|注册文件。|
|[IRegistrar::FileUnregister](#fileunregister)|取消注册该文件。|
|[IRegistrar::StringRegister](#stringregister)|将字符串的注册。|
|[IRegistrar::StringUnregister](#stringunregister)|在字符串中取消注册|
|[IRegistrar::ResourceRegister](#resourceregister)|注册资源。|
|[IRegistrar::ResourceUnregister](#resourceunregister)|注销该资源。|

## <a name="requirements"></a>要求

**标头：** atlifase.h

##  <a name="resourceregistersz"></a>  IRegistrar::ResourceRegisterSz

注册资源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="resourceunregistersz"></a>  IRegistrar::ResourceUnregisterSz

注销该资源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="fileregister"></a>  IRegistrar::FileRegister

注册文件。

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

##  <a name="fileunregister"></a>  IRegistrar::FileUnregister

取消注册该文件。

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

##  <a name="stringregister"></a>  IRegistrar::StringRegister

注册指定的字符串数据。

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

##  <a name="stringunregister"></a>  IRegistrar::StringUnregister

取消注册指定的字符串数据。

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

##  <a name="resourceregister"></a>  IRegistrar::ResourceRegister

注册资源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="resourceunregister"></a>  IRegistrar::ResourceUnregister

注销该资源。

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>请参阅

[使用可替换参数（注册器预处理器）](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[Module 类](../../atl/atl-module-classes.md)<br/>
[注册表组件 （注册器）](../../atl/atl-registry-component-registrar.md)
