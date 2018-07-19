---
title: CAtlComModule 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b553a6b99afd2de34c11aa0ad8a979580177d042
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885057"
---
# <a name="catlcommodule-class"></a>CAtlComModule 类
此类实现的 COM 服务器模块。  
  
## <a name="syntax"></a>语法  
  
```
class CAtlComModule : public _ATL_COM_MODULE
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlComModule::CAtlComModule](#catlcommodule)|构造函数。|  
|[CAtlComModule:: ~ CAtlComModule](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlComModule::RegisterServer](#registerserver)|调用此方法以更新对象映射中的每个对象的系统注册表。|  
|[CAtlComModule::RegisterTypeLib](#registertypelib)|调用此方法来注册类型库。|  
|[CAtlComModule::UnregisterServer](#unregisterserver)|调用此方法来取消注册对象映射中的每个对象。|  
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|调用此方法以注销类型库。|  
  
## <a name="remarks"></a>备注  
 `CAtlComModule` 实现 COM 服务器模块，从而允许客户端访问模块的组件。  
  
 此类替换已过时[CComModule](../../atl/reference/ccommodule-class.md)的 atl。 早期版本中使用的类 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)  
  
 `CAtlComModule`  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
##  <a name="catlcommodule"></a>  CAtlComModule::CAtlComModule  
 构造函数。  
  
```
CAtlComModule() throw();
```  
  
### <a name="remarks"></a>备注  
 初始化模块。  
  
##  <a name="dtor"></a>  CAtlComModule:: ~ CAtlComModule  
 析构函数。  
  
```
~CAtlComModule();
```  
  
### <a name="remarks"></a>备注  
 释放所有类工厂。  
  
##  <a name="registerserver"></a>  CAtlComModule::RegisterServer  
 调用此方法以更新对象映射中的每个对象的系统注册表。  
  
```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>参数  
 *bRegTypeLib*  
 如果类型库的注册，则为 TRUE。 默认值为 FALSE。  
  
 *pCLSID*  
 指向要注册的对象的 CLSID。 如果将注册为 NULL （默认值），在对象映射中的所有对象。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 调用全局函数[AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver)。  
  
##  <a name="registertypelib"></a>  CAtlComModule::RegisterTypeLib  
 调用此方法来注册类型库。  
  
```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```  
  
### <a name="parameters"></a>参数  
 *lpszIndex*  
 格式字符串"\\\N"，其中 N 是类型库资源的整数索引。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 将类型库有关的信息添加到系统注册表。 如果模块实例包含多个类型库，则使用此方法的第一个版本以指定应使用哪些类型库。  
  
##  <a name="unregisterserver"></a>  CAtlComModule::UnregisterServer  
 调用此方法来取消注册对象映射中的每个对象。  
  
```
HRESULT UnregisterServer(
  BOOL bRegTypeLib = FALSE,  
  const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>参数  
 *bRegTypeLib*  
 如果类型库，则要注销，则为 TRUE。 默认值为 FALSE。  
  
 *pCLSID*  
 指向要注销的对象的 CLSID。 如果为 NULL （默认值），在对象映射中的所有对象将为未注册。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 调用全局函数[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)。  
  
##  <a name="unregistertypelib"></a>  CAtlComModule::UnRegisterTypeLib  
 调用此方法以注销类型库。  
  
```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```  
  
### <a name="parameters"></a>参数  
 *lpszIndex*  
 格式字符串"\\\N"，其中 N 是类型库资源的整数索引。  
  
### <a name="remarks"></a>备注  
 从系统注册表中删除有关类型库的信息。 如果模块实例包含多个类型库，则使用此方法的第一个版本以指定应使用哪些类型库。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
## <a name="see-also"></a>请参阅  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)   
 [类概述](../../atl/atl-class-overview.md)
