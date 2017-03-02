---
title: "CAtlComModule 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CAtlComModule
- CAtlComModule
- ATL::CAtlComModule
dev_langs:
- C++
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
caps.latest.revision: 19
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 6b933b5388fccc2dc0e31d035aa7eb56de3b1866
ms.lasthandoff: 02/24/2017

---
# <a name="catlcommodule-class"></a>CAtlComModule 类
此类实现 COM 服务器模块。  
  
## <a name="syntax"></a>语法  
  
```
class CAtlComModule : public _ATL_COM_MODULE
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlComModule::CAtlComModule](#catlcommodule)|构造函数。|  
|[CAtlComModule:: ~ CAtlComModule](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlComModule::RegisterServer](#registerserver)|调用此方法以更新系统注册表中有在对象映射中的每个对象。|  
|[CAtlComModule::RegisterTypeLib](#registertypelib)|调用此方法来注册类型库。|  
|[CAtlComModule::UnregisterServer](#unregisterserver)|调用此方法来取消注册在对象映射中的每个对象。|  
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|调用此方法可注销类型库。|  
  
## <a name="remarks"></a>备注  
 `CAtlComModule`实现 COM 服务器模块，从而使客户端来访问该模块的组件。  
  
 此类替换已过时[CComModule](../../atl/reference/ccommodule-class.md)的 atl。 早期版本中使用的类 请参阅[ATL Module 类](../../atl/atl-module-classes.md)的更多详细信息。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)  
  
 `CAtlComModule`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="a-namecatlcommodulea--catlcommodulecatlcommodule"></a><a name="catlcommodule"></a>CAtlComModule::CAtlComModule  
 构造函数。  
  
```
CAtlComModule() throw();
```  
  
### <a name="remarks"></a>备注  
 初始化模块。  
  
##  <a name="a-namedtora--catlcommodulecatlcommodule"></a><a name="dtor"></a>CAtlComModule:: ~ CAtlComModule  
 析构函数。  
  
```
~CAtlComModule();
```  
  
### <a name="remarks"></a>备注  
 释放所有类工厂。  
  
##  <a name="a-nameregisterservera--catlcommoduleregisterserver"></a><a name="registerserver"></a>CAtlComModule::RegisterServer  
 调用此方法以更新系统注册表中有在对象映射中的每个对象。  
  
```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>参数  
 `bRegTypeLib`  
 如果要注册类型库，则为 TRUE。 默认值为 FALSE。  
  
 `pCLSID`  
 指向要注册的对象的 CLSID。 如果将注册为 NULL （默认值），在对象映射中的所有对象。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 调用全局函数[AtlComModuleRegisterServer](http://msdn.microsoft.com/library/d11a0c91-0c56-4b1b-a5f5-1287970f798b)。  
  
##  <a name="a-nameregistertypeliba--catlcommoduleregistertypelib"></a><a name="registertypelib"></a>CAtlComModule::RegisterTypeLib  
 调用此方法来注册类型库。  
  
```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```  
  
### <a name="parameters"></a>参数  
 `lpszIndex`  
 格式字符串"\\\N"，其中 N 是类型库资源的整数索引。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 将类型库的信息添加到系统注册表。 如果模块实例中包含多个类型库，使用此方法的第一个版本以指定应使用哪些类型库。  
  
##  <a name="a-nameunregisterservera--catlcommoduleunregisterserver"></a><a name="unregisterserver"></a>CAtlComModule::UnregisterServer  
 调用此方法来取消注册在对象映射中的每个对象。  
  
```
HRESULT UnregisterServer(
  BOOL bRegTypeLib = FALSE,  
  const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>参数  
 `bRegTypeLib`  
 如果要将注销类型库，则为 TRUE。 默认值为 FALSE。  
  
 `pCLSID`  
 指向要取消注册的对象的 CLSID。 如果为 NULL （默认值），在对象映射中的所有对象将为未注册。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 调用全局函数[AtlComModuleUnregisterServer](http://msdn.microsoft.com/library/c4ef3da4-def7-4aaf-b005-573a02e389d5)。  
  
##  <a name="a-nameunregistertypeliba--catlcommoduleunregistertypelib"></a><a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib  
 调用此方法可注销类型库。  
  
```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```  
  
### <a name="parameters"></a>参数  
 `lpszIndex`  
 格式字符串"\\\N"，其中 N 是类型库资源的整数索引。  
  
### <a name="remarks"></a>备注  
 从系统注册表中删除有关类型库的信息。 如果模块实例中包含多个类型库，使用此方法的第一个版本以指定应使用哪些类型库。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
## <a name="see-also"></a>另请参阅  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)   
 [类概述](../../atl/atl-class-overview.md)

