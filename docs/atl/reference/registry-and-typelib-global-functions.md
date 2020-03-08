---
title: 注册表和类型库全局函数
ms.date: 03/27/2019
f1_keywords:
- atlbase/ATL::AtlGetPerUserRegistration
- afxpriv/ATL::AfxRegCreateKey
- afxpriv/ATL::AfxRegDeleteKey
- atlbase/ATL::AtlRegisterTypeLib
- afxpriv/ATL::AfxRegOpenKey
- afxpriv/ATL::AfxRegOpenKeyEx
- afxdisp/ATL::AfxUnregisterPreviewHandler
- atlbase/ATL::AtlSetPerUserRegistration
- atlbase/ATL::AtlUnRegisterTypeLib
- atlbase/ATL::AtlLoadTypeLib
- atlbase/ATL::AtlUpdateRegistryFromResourceD
- atlbase/ATL::RegistryDataExchange
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
ms.openlocfilehash: c5fdaceb47b6cd09dd9d66f26af1337a8dc6bbae
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863152"
---
# <a name="registry-and-typelib-global-functions"></a>注册表和类型库全局函数

这些函数为加载和注册类型库提供支持。

> [!IMPORTANT]
>  下表中列出的函数不能用于在 Windows 运行时中执行的应用程序。

|||
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|创建指定的注册表项。|
|[AfxRegDeleteKey](#afxregdeletekey)|删除指定的注册表项。|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|用于注册预览处理程序的帮助程序。|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| 用于注销预览处理程序的帮助程序。 |
|[AtlRegisterTypeLib](#atlregistertypelib)|调用此函数可注册类型库。|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|调用此函数以取消注册类型库|
|[AfxRegOpenKey](#afxregopenkey)|打开指定的注册表项。|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|打开指定的注册表项。|
|[AtlLoadTypeLib](#atlloadtypelib)|调用此函数可加载类型库。|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|调用此函数可从提供的资源中更新注册表。|
|[RegistryDataExchange](#registrydataexchange)|调用此函数可在系统注册表中进行读取或写入。 由[注册表数据交换宏](../../atl/reference/registry-data-exchange-macros.md)调用。|

这些函数控制程序用来存储信息的注册表中的节点。

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|检索应用程序是否将注册表访问重定向到**HKEY_CURRENT_USER** （ **HKCU**）节点。|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|设置应用程序是否将注册表访问重定向到**HKEY_CURRENT_USER** （ **HKCU**）节点。|

### <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration

使用此函数可确定应用程序是否将注册表访问重定向到**HKEY_CURRENT_USER** （**HKCU**）节点。

### <a name="syntax"></a>语法

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>参数

*pEnabled*<br/>
弄TRUE 指示将注册表信息定向到**HKCU**节点;FALSE 表示应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** （**HKCR**）。

### <a name="return-value"></a>返回值

如果方法成功，则 S_OK; 否则，如果发生错误，则为 HRESULT 错误代码。

### <a name="remarks"></a>备注

默认情况下，不启用注册表重定向。 如果启用此选项，注册表访问将重定向到**HKEY_CURRENT_USER \software\classes**。

重定向不是全局的。 此注册表重定向仅影响 MFC 和 ATL 框架。

### <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="afxregcreatekey"></a>AfxRegCreateKey

创建指定的注册表项。

### <a name="syntax"></a>语法

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*hKey*<br/>
打开的注册表项的句柄。

*lpSubKey*<br/>
此函数打开或创建的键的名称。

*phkResult*<br/>
指向一个变量的指针，该变量接收已打开或已创建的键的句柄。

*pTM*<br/>
指向 `CAtlTransactionManager` 对象的指针。

### <a name="return-value"></a>返回值

如果该函数成功，则返回值为 ERROR_SUCCESS。 如果函数失败，则返回值为 Winerror.h 中定义的非零错误代码。

### <a name="requirements"></a>要求

**标头：** afxpriv.h

## <a name="afxregdeletekey"></a>AfxRegDeleteKey

删除指定的注册表项。

### <a name="syntax"></a>语法

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*hKey*<br/>
打开的注册表项的句柄。

*lpSubKey*<br/>
要删除的密钥的名称。

*pTM*<br/>
指向 `CAtlTransactionManager` 对象的指针。

### <a name="return-value"></a>返回值

如果该函数成功，则返回值为 ERROR_SUCCESS。 如果函数失败，则返回值为 Winerror.h 中定义的非零错误代码。

### <a name="requirements"></a>要求

**标头：** afxpriv.h

## <a name="afxregisterpreviewhandler"></a>

用于注册预览处理程序的帮助程序。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>参数

*lpszCLSID*<br/>
指定处理程序的 CLSID。

*lpszShortTypeName*<br/>
指定处理程序的 ProgID。

*lpszFilterExt*<br/>
指定注册到此处理程序的文件扩展名。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

##  <a name="atlregistertypelib"></a>AtlRegisterTypeLib

调用此函数可注册类型库。

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>参数

*hInstTypeLib*<br/>
模块实例的句柄。

*lpszIndex*<br/>
格式为 "\\\N" 的字符串，其中 N 是类型库资源的整数索引。 如果不需要索引，则可以为 NULL。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)和[CAtlComModule：： RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib)使用此 helper 函数。

### <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="afxregopenkey"></a>AfxRegOpenKey

打开指定的注册表项。

### <a name="syntax"></a>语法

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*hKey*<br/>
打开的注册表项的句柄。

*lpSubKey*<br/>
此函数打开或创建的键的名称。

*phkResult*<br/>
指向一个变量的指针，该变量接收创建的键的句柄。

*pTM*<br/>
指向 `CAtlTransactionManager` 对象的指针。

### <a name="return-value"></a>返回值

如果该函数成功，则返回值为 ERROR_SUCCESS。 如果函数失败，则返回值为 Winerror.h 中定义的非零错误代码。

### <a name="requirements"></a>要求

**标头：** afxpriv.h

## <a name="afxregopenkeyex"></a>AfxRegOpenKeyEx

打开指定的注册表项。

### <a name="syntax"></a>语法

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*hKey*<br/>
打开的注册表项的句柄。

*lpSubKey*<br/>
此函数打开或创建的键的名称。

*ulOptions*<br/>
此参数为保留参数，必须为零。

*samDesired*<br/>
指定对密钥所需的访问权限的掩码。

*phkResult*<br/>
指向一个变量的指针，该变量接收打开的键的句柄。

*pTM*<br/>
指向 `CAtlTransactionManager` 对象的指针。

### <a name="return-value"></a>返回值

如果该函数成功，则返回值为 ERROR_SUCCESS。 如果函数失败，则返回值为 Winerror.h 中定义的非零错误代码。

### <a name="requirements"></a>要求

**标头：** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler

用于注销预览处理程序的帮助程序。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>参数

*lpszCLSID*<br/>
指定要注销的处理程序的 CLSID。

### <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration

设置应用程序是否将注册表访问重定向到**HKEY_CURRENT_USER** （**HKCU**）节点。

### <a name="syntax"></a>语法

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
中TRUE 指示将注册表信息定向到**HKCU**节点;FALSE 表示应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** （**HKCR**）。

### <a name="return-value"></a>返回值

如果方法成功，则 S_OK; 否则，如果发生错误，则为 HRESULT 错误代码。

### <a name="remarks"></a>备注

默认情况下，不启用注册表重定向。 如果启用此选项，注册表访问将重定向到**HKEY_CURRENT_USER \software\classes**。

重定向不是全局的。 此注册表重定向仅影响 MFC 和 ATL 框架。

### <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib

调用此函数可注销类型库。

### <a name="syntax"></a>语法

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>参数

*hInstTypeLib*<br/>
模块实例的句柄。

*lpszIndex*<br/>
格式为 "\\\N" 的字符串，其中 N 是类型库资源的整数索引。 如果不需要索引，则可以为 NULL。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

此 helper 函数可由[CAtlComModule：： UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib)和[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)使用。

### <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="atlloadtypelib"></a>AtlLoadTypeLib

调用此函数可加载类型库。

### <a name="syntax"></a>语法

```
ATLINLINE ATLAPI AtlLoadTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex,
    BSTR* pbstrPath,
    ITypeLib** ppTypeLib);
```

### <a name="parameters"></a>参数

*hInstTypeLib*<br/>
与类型库关联的模块的句柄。

*lpszIndex*<br/>
格式为 "\\\N" 的字符串，其中 N 是类型库资源的整数索引。 如果不需要索引，则可以为 NULL。

*pbstrPath*<br/>
成功返回时，包含与类型库关联的模块的完整路径。

*ppTypeLib*<br/>
成功返回时，包含指向已加载类型库的指针的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

此 helper 函数由[AtlRegisterTypeLib](#atlregistertypelib)和[AtlUnRegisterTypeLib](#atlunregistertypelib)使用。

##  <a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD

此函数已在 Visual Studio 2013 中弃用，并已从 Visual Studio 2015 中删除。

```
<removed>
```

##  <a name="registrydataexchange"></a>RegistryDataExchange

调用此函数可在系统注册表中进行读取或写入。

### <a name="syntax"></a>语法

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>参数

*五*<br/>
指向当前对象的指针。

*rdxOp*<br/>
一个枚举值，该值指示函数应执行的操作。 有关允许的值，请参阅 "备注" 部分中的表。

*pItem*<br/>
指向要从注册表读取或写入注册表的数据的指针。 数据还可以表示要从注册表中删除的密钥。 默认值为 NULL。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

宏[BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map)和[END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map)展开到调用 `RegistryDataExchange`的函数。

下表显示了指示函数应执行的操作的可能的枚举值：

|枚举值|操作|
|----------------|---------------|
|eReadFromReg|从注册表读取数据。|
|eWriteToReg|将数据写入注册表。|
|eDeleteFromReg|删除注册表中的密钥。|

### <a name="requirements"></a>要求

**标头：** atlbase。h

## <a name="see-also"></a>另请参阅

[函数](atl-functions.md)<br/>
[注册表数据交换宏](registry-data-exchange-macros.md)
