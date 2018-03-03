---
title: "CAtlWinModule 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dcaf3d6573432b7f6f16826b2551a7e9330abed9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="catlwinmodule-class"></a>CAtlWinModule 类
此类为 ATL 窗口化组件提供支持。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CAtlWinModule : public _ATL_WIN_MODULE
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|构造函数。|  
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|添加数据对象。|  
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|返回指向窗口模块数据对象的指针。|  
  
## <a name="remarks"></a>备注  
 此类所有 ATL 类需要窗口化功能都提供支持。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)  
  
 `CAtlWinModule`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
##  <a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData  
 此方法初始化并添加`_AtlCreateWndData`结构。  
  
```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```  
  
### <a name="parameters"></a>参数  
 `pData`  
 指向`_AtlCreateWndData`结构来初始化和添加到当前的模块。  
  
 `pObject`  
 指针指向的对象**这**指针。  
  
### <a name="remarks"></a>备注  
 此方法调用[AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata)哪些初始化[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)结构。 此结构将存储**这**指针，用于获取窗口过程中的类实例。  
  
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
 返回一个指向`_AtlCreateWndData`与之前添加的结构[CAtlWinModule::AddCreateWndData](#addcreatewnddata)，或如果没有对象，则可为 NULL。  
  
## <a name="see-also"></a>请参阅  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)   
 [类概述](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)
