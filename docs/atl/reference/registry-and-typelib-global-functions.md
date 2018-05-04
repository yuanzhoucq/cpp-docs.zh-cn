---
title: 注册表和类型库全局函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb0a89ecf8bb81e515703abe819bb1edfbf80d59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="registry-and-typelib-global-functions"></a>注册表和类型库全局函数
这些函数提供用于加载和注册类型库的支持。  
  
> [!IMPORTANT]
>  下表中列出的函数不能在 Windows 运行时中执行的应用程序。  
  
|||  
|-|-|  
|[AfxRegCreateKey](#afxrefcreatekey)|创建指定的注册表项。|
|[AfxRegDeleteKey](#afxrefdeletekey)|删除指定的注册表项。|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|用于注册预览处理程序的帮助程序。|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| 用于注销预览处理程序的帮助程序。 |
|[AtlRegisterTypeLib](#atlregistertypelib)|调用此函数可注册类型库。|  
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|调用此函数可注销类型库|  
|[AfxRegOpenKey](#afxregopenkey)|打开指定的注册表项。|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|打开指定的注册表项。|
|[AtlLoadTypeLib](#atlloadtypelib)|调用此函数可加载类型库。|  
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|调用此函数可从提供的资源中更新注册表。|  
|[RegistryDataExchange](#registrydataexchange)|调用此函数可在系统注册表中进行读取或写入。 由调用[注册表数据交换宏](../../atl/reference/registry-data-exchange-macros.md)。|  
  
 这些函数控制程序使用来存储信息的注册表中的哪个节点。  
  
|||  
|-|-|  
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|检索是否应用程序将注册表访问重定向**HKEY_CURRENT_USER** ( **HKCU**) 节点。|  
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|设置是否应用程序将注册表访问重定向**HKEY_CURRENT_USER** ( **HKCU**) 节点。|  

### <a name="requirements"></a>要求  
 **标头：** atlbase.h

## <a name="atlgetperuserregistration"></a> AtlGetPerUserRegistration
使用此函数可确定应用程序是否将注册表访问重定向**HKEY_CURRENT_USER** (**HKCU**) 节点。  
  
### <a name="syntax"></a>语法  
  
```  
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);  
```  
  
### <a name="parameters"></a>参数  
 [out] `pEnabled`  
 `TRUE` 指示注册表信息将定向至**HKCU**节点;`FALSE`指示，则应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** (**HKCR**)。  
  
### <a name="return-value"></a>返回值  
 `S_OK` 如果此方法成功，否则`HRESULT`如果发生错误的错误代码。  
  
### <a name="remarks"></a>备注  
 默认情况下不启用注册表重定向。 如果启用此选项，注册表访问重定向到**HKEY_CURRENT_USER\Software\Classes**。  
  
 重定向不是全局设置。 仅 MFC 和 ATL 框架受此注册表重定向。  
  
### <a name="requirements"></a>要求  
 **标头：** atlbase.h  

 ## <a name="afxregcreatekey"></a> AfxRegCreateKey
 创建指定的注册表项。  
  
### <a name="syntax"></a>语法  
  
```  
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>参数  
 `hKey`  
 打开注册表项句柄。  
  
 `lpSubKey`  
 此函数将打开或创建的密钥的名称。  
  
 `phkResult`  
 指向接收的打开或创建密钥的句柄的变量的指针。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则返回值是 ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义一个非零错误代码。  

### <a name="requirements"></a>要求  
 **标头：** afxpriv.h  

## <a name="afxregdeletekey"></a> AfxRegDeleteKey
删除指定的注册表项。  
  
### <a name="syntax"></a>语法  
  
```  
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>参数  
 `hKey`  
 打开注册表项句柄。  
  
 `lpSubKey`  
 要删除的密钥名称。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则返回值是 ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义一个非零错误代码。  
  
### <a name="requirements"></a>要求  
 **标头：** afxpriv.h  

## <a name="afxregisterpreviewhandler"></a>
用于注册预览处理程序的帮助程序。  
  
### <a name="syntax"></a>语法  
  
```  
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);  
```  
  
### <a name="parameters"></a>参数  
 `lpszCLSID`  
 指定处理程序的 CLSID。  
  
 `lpszShortTypeName`  
 指定处理程序的 ProgID。  
  
 `lpszFilterExt`  
 指定注册到此处理程序的文件扩展名。  
  
### <a name="requirements"></a>要求  
 **标头：** afxdisp.h   

##  <a name="atlregistertypelib"></a>  AtlRegisterTypeLib  
 调用此函数可注册类型库。  
  
  
```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>参数  
 `hInstTypeLib`  
 模块实例的句柄。  
  
 `lpszIndex`  
 格式字符串"\\\N"，其中 N 是类型库资源的整数索引。 如果没有索引是必需的则可以为 NULL。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 利用此帮助器函数[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)和[CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib)。  
### <a name="requirements"></a>要求  
 **标头：** atlbase.h

 ## <a name="afxregopenkey"></a> AfxRegOpenKey
 打开指定的注册表项。  
  
### <a name="syntax"></a>语法  
  
```  
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>参数  
 `hKey`  
 打开注册表项句柄。  
  
 `lpSubKey`  
 此函数将打开或创建的密钥的名称。  
  
 `phkResult`  
 指向接收创建的密钥的句柄的变量的指针。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则返回值是 ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义一个非零错误代码。  
  
### <a name="requirements"></a>要求  
 **标头：** afxpriv.h  

## <a name="afxregopenkeyex"></a>  AfxRegOpenKeyEx
打开指定的注册表项。 

### <a name="syntax"></a>语法  
  
```  
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>参数  
 `hKey`  
 打开注册表项句柄。  
  
 `lpSubKey`  
 此函数将打开或创建的密钥的名称。  
  
 `ulOptions`  
 此参数是保留，必须为零。  
  
 `samDesired`  
 指定的键的所需的访问权限的掩码。  
  
 `phkResult`  
 指向接收打开密钥的句柄的变量的指针。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则返回值是 ERROR_SUCCESS。 如果函数失败，返回值是在 Winerror.h 中定义一个非零错误代码。  
  
### <a name="requirements"></a>要求  
 **标头：** afxpriv.h  

 ## <a name="afxunregisterpreviewhandler"></a> AfxUnregisterPreviewHandler
 用于注销预览处理程序的帮助程序。  
  
### <a name="syntax"></a>语法  
  
```  
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);  
```  
  
### <a name="parameters"></a>参数  
 `lpszCLSID`  
 指定要注销的处理程序的 CLSID。  
  
### <a name="requirements"></a>要求  
 **标头：** afxdisp.h  

## <a name="atlsetperuserregistration"></a> AtlSetPerUserRegistration
设置是否应用程序将注册表访问重定向**HKEY_CURRENT_USER** (**HKCU**) 节点。  
  
### <a name="syntax"></a>语法  
  
```  
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);  
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE` 指示注册表信息将定向至**HKCU**节点;`FALSE`指示，则应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** (**HKCR**)。  
  
### <a name="return-value"></a>返回值  
 `S_OK` 如果此方法成功，否则`HRESULT`如果发生错误的错误代码。  
  
### <a name="remarks"></a>备注  
 默认情况下不启用注册表重定向。 如果启用此选项，注册表访问重定向到**HKEY_CURRENT_USER\Software\Classes**。  
  
 重定向不是全局设置。 仅 MFC 和 ATL 框架受此注册表重定向。  
### <a name="requirements"></a>要求  
 **标头：** atlbase.h  

##  <a name="atlunregistertypelib"></a>  AtlUnRegisterTypeLib  
 调用此函数可注销类型库。  
  
### <a name="syntax"></a>语法  
```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib, 
    LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>参数  
 `hInstTypeLib`  
 模块实例的句柄。  
  
 `lpszIndex`  
 格式字符串"\\\N"，其中 N 是类型库资源的整数索引。 如果没有索引是必需的则可以为 NULL。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 利用此帮助器函数[CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib)和[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)。  
### <a name="requirements"></a>要求  
 **标头：** atlbase.h

##  <a name="atlloadtypelib"></a>  AtlLoadTypeLib  
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
 `hInstTypeLib`  
 与类型库关联的模块的句柄。  
  
 `lpszIndex`  
 格式字符串"\\\N"，其中 N 是类型库资源的整数索引。 如果没有索引是必需的则可以为 NULL。  
  
 *pbstrPath*  
 在成功返回时，包含与类型库关联的模块的完整路径。  
  
 `ppTypeLib`  
 在成功返回时，包含指向对加载的类型库的指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 利用此帮助器函数[AtlRegisterTypeLib](#atlregistertypelib)和[AtlUnRegisterTypeLib](#atlunregistertypelib)。  
  
##  <a name="atlupdateregistryfromresourced"></a>  AtlUpdateRegistryFromResourceD  
 此函数已在 Visual Studio 2013 中弃用，并已从 Visual Studio 2015 中删除。  
  
```
<removed>
```  
  

  
##  <a name="registrydataexchange"></a>  RegistryDataExchange  
 调用此函数可在系统注册表中进行读取或写入。  

### <a name="syntax"></a>语法  
```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```  
  
### <a name="parameters"></a>参数  
 *PT*  
 指向当前对象的指针。  
  
 *rdxOp*  
 枚举值，该值指示哪个操作应执行该函数。 请参阅允许的值备注部分中的表。  
  
 `pItem`  
 指向要读取或写入注册表的数据的指针。 数据还可以表示一个密钥，以从注册表中删除。 默认值为 NULL。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 宏[BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map)和[END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map)展开到调用的函数， `RegistryDataExchange`。  
  
 可能的枚举值，用于指示操作函数应执行以下表所示：  
  
|枚举值|操作|  
|----------------|---------------|  
|eReadFromReg|从注册表中读取数据。|  
|eWriteToReg|将数据写入到注册表。|  
|eDeleteFromReg|从注册表中删除密钥。|  
  
### <a name="requirements"></a>要求  
 **标头：** atlbase.h

## <a name="see-also"></a>请参阅  
 [函数](atl-functions.md)[注册表数据交换宏](registry-data-exchange-macros.md)





