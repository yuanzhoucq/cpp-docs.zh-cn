---
title: IRegistrar 接口
ms.date: 02/01/2017
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
ms.openlocfilehash: e347bdba1656a53cd705123a26650dad50d3892f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423050"
---
# <a name="iregistrar-interface"></a>IRegistrar 接口

此接口是在 atliface 中定义的，由 CAtlModule 成员函数（如[UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)）在内部使用。

## <a name="syntax"></a>语法

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>备注

有关更多详细信息，请参阅主题[使用可替换参数（注册器的预处理器）](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) 。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|注册资源。 |
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| 取消注册资源。|
|[IRegistrar::FileRegister](#fileregister)|注册文件。|
|[IRegistrar::FileUnregister](#fileunregister)|取消注册文件。|
|[IRegistrar::StringRegister](#stringregister)|注册字符串。|
|[IRegistrar::StringUnregister](#stringunregister)|取消注册字符串|
|[IRegistrar::ResourceRegister](#resourceregister)|注册资源。|
|[IRegistrar::ResourceUnregister](#resourceunregister)|取消注册资源。|

## <a name="requirements"></a>要求

**标头：** atlifase

##  <a name="resourceregistersz"></a>IRegistrar::ResourceRegisterSz

注册资源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="resourceunregistersz"></a>IRegistrar::ResourceUnregisterSz

取消注册资源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="fileregister"></a>IRegistrar::FileRegister

注册文件。

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

##  <a name="fileunregister"></a>IRegistrar::FileUnregister

取消注册文件。

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

##  <a name="stringregister"></a>IRegistrar::StringRegister

注册指定的字符串数据。

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

##  <a name="stringunregister"></a>IRegistrar::StringUnregister

注销指定的字符串数据。

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

##  <a name="resourceregister"></a>IRegistrar::ResourceRegister

注册资源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="resourceunregister"></a>IRegistrar::ResourceUnregister

取消注册资源。

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>另请参阅

[使用可替换参数（注册器预处理器）](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[Module 类](../../atl/atl-module-classes.md)<br/>
[注册表组件（注册器）](../../atl/atl-registry-component-registrar.md)
