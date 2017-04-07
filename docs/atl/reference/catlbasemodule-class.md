---
title: "CAtlBaseModule 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
dev_langs:
- C++
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
caps.latest.revision: 18
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
ms.openlocfilehash: 4897f6cf7e12a18401720ad663c90491bb0e599d
ms.lasthandoff: 02/24/2017

---
# <a name="catlbasemodule-class"></a>CAtlBaseModule 类
此类进行实例化每个 ATL 项目中。  
  
## <a name="syntax"></a>语法  
  
```
class CAtlBaseModule : public _ATL_BASE_MODULE
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|将资源实例添加到的存储句柄的列表。|  
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|返回指定的资源实例的句柄。|  
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|返回从模块实例`CAtlBaseModule`对象。|  
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|返回从资源实例`CAtlBaseModule`对象。|  
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|从存储句柄的列表中删除资源实例。|  
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|设置的资源实例`CAtlBaseModule`对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|指示是否出现故障的模块初始化的变量。|  
  
## <a name="remarks"></a>备注  
 一个实例`CAtlBaseModule`命名的 _AtlBaseModule 是否出现在每个 ATL 项目，其中包含模块实例的句柄、 包含资源 （即默认情况下，同一个），该模块，提供主要资源的模块的句柄数组的句柄。 `CAtlBaseModule`可以安全地从多个线程访问。  
  
 此类替换已过时[CComModule](../../atl/reference/ccommodule-class.md)的 atl。 早期版本中使用的类  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)  
  
 `CAtlBaseModule`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcore.h  
  
##  <a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance  
 将资源实例添加到的存储句柄的列表。  
  
```
bool AddResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>参数  
 `hInst`  
 要添加的资源实例。  
  
### <a name="return-value"></a>返回值  
 如果该资源已成功则返回 true，添加 false 否则。  
  
##  <a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule  
 构造函数。  
  
```
CAtlBaseModule() throw();
```  
  
### <a name="remarks"></a>备注  
 创建 `CAtlBaseModule`。  
  
##  <a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt  
 返回指定的资源实例的句柄。  
  
```
HINSTANCE GetHInstanceAt(int i) throw();
```  
  
### <a name="parameters"></a>参数  
 *i*  
 资源实例数。  
  
### <a name="return-value"></a>返回值  
 如果没有对应的资源实例存在，请返回的句柄资源实例，或者为 NULL。  
  
##  <a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance  
 返回从模块实例`CAtlBaseModule`对象。  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的模块实例。  
  
##  <a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance  
 返回的资源实例。  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的资源实例。  
  
##  <a name="m_binitfailed"></a>CAtlBaseModule::m_bInitFailed  
 指示是否出现故障的模块初始化的变量。  
  
```
static bool m_bInitFailed;
```  
  
### <a name="remarks"></a>备注  
 如果该模块初始化，false 如果它无法初始化，则为 true。  
  
##  <a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance  
 从存储句柄的列表中删除资源实例。  
  
```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>参数  
 `hInst`  
 要删除的资源实例。  
  
### <a name="return-value"></a>返回值  
 如果资源否则是已成功删除，则返回 false，则返回 true。  
  
##  <a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance  
 设置的资源实例`CAtlBaseModule`对象。  
  
```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>参数  
 `hInst`  
 新的资源实例。  
  
### <a name="return-value"></a>返回值  
 返回的已更新的资源实例。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)

