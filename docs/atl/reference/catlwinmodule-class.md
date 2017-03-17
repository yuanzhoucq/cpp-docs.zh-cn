---
title: "CAtlWinModule 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
caps.latest.revision: 20
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 6db3ae9e610605524683e984f2aba602b1daf0d4
ms.lasthandoff: 02/24/2017

---
# <a name="catlwinmodule-class"></a>CAtlWinModule 类
此类为 ATL 窗口化组件提供支持。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CAtlWinModule : public _ATL_WIN_MODULE
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|构造函数。|  
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|添加一个数据对象。|  
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|返回到窗口模块数据对象的指针。|  
  
## <a name="remarks"></a>备注  
 此类的所有 ATL 类需要窗口功能提供支持。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)  
  
 `CAtlWinModule`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData  
 此方法初始化，并添加`_AtlCreateWndData`结构。  
  
```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```  
  
### <a name="parameters"></a>参数  
 `pData`  
 指向`_AtlCreateWndData`结构要初始化和添加到当前的模块。  
  
 `pObject`  
 指针指向的对象**这**指针。  
  
### <a name="remarks"></a>备注  
 此方法调用[AtlWinModuleAddCreateWndData](http://msdn.microsoft.com/library/8463a6ed-07ea-4aad-92ec-ded681601b32)哪些初始化[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构。 此结构将存储**这**指针，用于获取窗口过程中的类实例。  
  
##  <a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule  
 构造函数。  
  
```
CAtlWinModule();
```  
  
### <a name="remarks"></a>备注  
 如果初始化失败， **EXCEPTION_NONCONTINUABLE**引发异常。  
  
##  <a name="dtor"></a>CAtlWinModule:: ~ CAtlWinModule  
 析构函数。  
  
```
~CAtlWinModule();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData  
 此方法返回一个指向`_AtlCreateWndData`结构。  
  
```
void* ExtractCreateWndData();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向`_AtlCreateWndData`与以前添加的结构[CAtlWinModule::AddCreateWndData](#addcreatewnddata)，或如果没有对象，则可为 NULL。  
  
## <a name="see-also"></a>另请参阅  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)   
 [类概述](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)

