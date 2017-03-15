---
title: "注册表和类型库全局函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9d454f2eac1b29785fe40a480fc43c7c34a861a3
ms.lasthandoff: 02/24/2017

---
# <a name="registry-and-typelib-global-functions"></a>注册表和类型库全局函数
这些函数提供用于加载和注册类型库的支持。  
  
> [!IMPORTANT]
>  下表中列出的函数不能用于应用程序中执行[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlRegisterTypeLib](#atlregistertypelib)|调用此函数可注册类型库。|  
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|调用此函数可注销类型库|  
|[AtlLoadTypeLib](#atlloadtypelib)|调用此函数可加载类型库。|  
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|调用此函数可从提供的资源中更新注册表。|  
|[RegistryDataExchange](#registrydataexchange)|调用此函数可在系统注册表中进行读取或写入。 由调用[注册表数据交换宏](../../atl/reference/registry-data-exchange-macros.md)。|  
  
 这些函数来控制该程序使用来存储信息的注册表中的哪个节点。  
  
|||  
|-|-|  
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|检索应用程序将注册表访问重定向是否**HKEY_CURRENT_USER** ( **HKCU**) 节点。|  
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|设置是否应用程序将注册表访问重定向**HKEY_CURRENT_USER** ( **HKCU**) 节点。|  

### <a name="requirements"></a>要求  
 **标头︰** atlbase.h

## <a name="a-nameatlgetperuserregistrationa-atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration
使用此函数可确定应用程序是否将注册表访问重定向**HKEY_CURRENT_USER** (**HKCU**) 节点。  
  
### <a name="syntax"></a>语法  
  
```  
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);  
```  
  
### <a name="parameters"></a>参数  
 [out] `pEnabled`  
 `TRUE`指示注册表信息将定向至**HKCU**节点;`FALSE`指示，则应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** (**HKCR**)。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果该方法成功，否则`HRESULT`如果发生错误的错误代码。  
  
### <a name="remarks"></a>备注  
 默认情况下不启用注册表重定向。 如果启用此选项时，注册表访问重定向到**HKEY_CURRENT_USER\Software\Classes**。  
  
 重定向不是全局设置。 仅 MFC 和 ATL 框架受此注册表重定向。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlbase.h  

##  <a name="a-nameatlregistertypeliba--atlregistertypelib"></a><a name="atlregistertypelib"></a>AtlRegisterTypeLib  
 调用此函数可注册类型库。  
  
  
```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>参数  
 `hInstTypeLib`  
 模块实例的句柄。  
  
 `lpszIndex`  
 格式字符串"\\\N"，其中 N 是类型库资源的整数索引。 如果没有索引是必需的可以为 NULL。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 利用此帮助器函数[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)和[CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib)。  
### <a name="requirements"></a>要求  
 **标头︰** atlbase.h

## <a name="a-nameatlsetperuserregistrationa-atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration
设置是否应用程序将注册表访问重定向**HKEY_CURRENT_USER** (**HKCU**) 节点。  
  
### <a name="syntax"></a>语法  
  
```  
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);  
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`指示注册表信息将定向至**HKCU**节点;`FALSE`指示，则应用程序将注册表信息写入默认节点。 默认节点为**HKEY_CLASSES_ROOT** (**HKCR**)。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果该方法成功，否则`HRESULT`如果发生错误的错误代码。  
  
### <a name="remarks"></a>备注  
 默认情况下不启用注册表重定向。 如果启用此选项时，注册表访问重定向到**HKEY_CURRENT_USER\Software\Classes**。  
  
 重定向不是全局设置。 仅 MFC 和 ATL 框架受此注册表重定向。  
### <a name="requirements"></a>要求  
 **标头︰** atlbase.h  

##  <a name="a-nameatlunregistertypeliba--atlunregistertypelib"></a><a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib  
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
 格式字符串"\\\N"，其中 N 是类型库资源的整数索引。 如果没有索引是必需的可以为 NULL。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 利用此帮助器函数[CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib)和[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)。  
### <a name="requirements"></a>要求  
 **标头︰** atlbase.h

##  <a name="a-nameatlloadtypeliba--atlloadtypelib"></a><a name="atlloadtypelib"></a>AtlLoadTypeLib  
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
 格式字符串"\\\N"，其中 N 是类型库资源的整数索引。 如果没有索引是必需的可以为 NULL。  
  
 *pbstrPath*  
 在成功返回时，包含与类型库关联的模块的完整路径。  
  
 `ppTypeLib`  
 在成功返回时，包含指向对加载的类型库的指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 利用此帮助器函数[AtlRegisterTypeLib](#atlregistertypelib)和[AtlUnRegisterTypeLib](#atlunregistertypelib)。  
  
##  <a name="a-nameatlupdateregistryfromresourceda--atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD  
 此函数已在 Visual Studio 2013 中弃用，并已从 Visual Studio 2015 中删除。  
  
```
<removed>
```  
  
### <a name="parameters"></a>参数  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameregistrydataexchangea--registrydataexchange"></a><a name="registrydataexchange"></a>RegistryDataExchange  
 调用此函数可在系统注册表中进行读取或写入。  

### <a name="syntax"></a>语法  
```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pT*  
 指向当前对象的指针。  
  
 *rdxOp*  
 枚举值，该值指示哪个操作应执行该函数。 请参阅备注部分的允许值中的表。  
  
 `pItem`  
 指向要读取或写入注册表的数据。 数据还可以表示一个密钥，以从注册表中删除。 默认值为 NULL。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 宏[BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map)和[END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map)展开到调用的函数， `RegistryDataExchange`。  
  
 下表中显示可能的枚举值，用于指示应执行该操作函数︰  
  
|枚举值|操作|  
|----------------|---------------|  
|eReadFromReg|从注册表中读取数据。|  
|eWriteToReg|向注册表写入数据。|  
|eDeleteFromReg|从注册表中删除的项。|  
  
### <a name="requirements"></a>要求  
 **标头︰** atlbase.h

## <a name="see-also"></a>另请参阅  
 [函数](atl-functions.md)
 [注册表数据交换宏](registry-data-exchange-macros.md)






