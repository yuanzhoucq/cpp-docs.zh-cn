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
ms.openlocfilehash: 98943fe294322715723bd91207a6f3320ca1ffb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329466"
---
# <a name="iregistrar-interface"></a>IRegistrar 接口

此接口在 atliface.h 中定义，并由 CAtlModule 成员函数（如[UpdateRegistryFromResourceD）](catlmodule-class.md#updateregistryfromresourced)在内部使用。

## <a name="syntax"></a>语法

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>备注

有关详细信息，请参阅["使用可替换参数（注册器的预处理器）"](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)主题。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I注册商：：资源注册](#resourceregistersz)|注册资源。 |
|[I注册人：：资源未注册](#resourceunregistersz)| 取消注册资源。|
|[I注册人：文件注册](#fileregister)|注册文件。|
|[I注册人：：文件未注册](#fileunregister)|取消注册该文件。|
|[IRegistrar：：字符串注册](#stringregister)|注册字符串。|
|[I注册人：：字符串未注册](#stringunregister)|取消注册字符串|
|[I注册人：：资源注册](#resourceregister)|注册资源。|
|[I注册人：：资源未注册](#resourceunregister)|取消注册资源。|

## <a name="requirements"></a>要求

**标题：** atlifase.h

## <a name="iregistrarresourceregistersz"></a><a name="resourceregistersz"></a>I注册商：：资源注册

注册资源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregistersz"></a><a name="resourceunregistersz"></a>I注册人：：资源未注册

取消注册资源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarfileregister"></a><a name="fileregister"></a>I注册人：文件注册

注册文件。

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarfileunregister"></a><a name="fileunregister"></a>I注册人：：文件未注册

取消注册该文件。

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarstringregister"></a><a name="stringregister"></a>IRegistrar：：字符串注册

注册指定的字符串数据。

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarstringunregister"></a><a name="stringunregister"></a>I注册人：：字符串未注册

取消注册指定的字符串数据。

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarresourceregister"></a><a name="resourceregister"></a>I注册人：：资源注册

注册资源。

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregister"></a><a name="resourceunregister"></a>I注册人：：资源未注册

取消注册资源。

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>另请参阅

[使用可替换参数（注册商的预处理器）](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[模块类](../../atl/atl-module-classes.md)<br/>
[注册表组件（注册器）](../../atl/atl-registry-component-registrar.md)
