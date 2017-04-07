---
title: "IRunnableObjectImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
dev_langs:
- C++
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: a9b2698c195ac5bd709e6d40d3c30008d3fa26d4
ms.lasthandoff: 02/24/2017

---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl 类
此类实现**IUnknown** ，并提供的默认实现[IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783)接口。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class IRunnableObjectImpl
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IRunnableObjectImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|返回正在运行的控件的 CLSID。 ATL 实现将 CLSID 设置为`GUID_NULL`，并返回**E_UNEXPECTED**。|  
|[IRunnableObjectImpl::IsRunning](#isrunning)|确定控件是否正在运行。 ATL 实现返回**TRUE**。|  
|[IRunnableObjectImpl::LockRunning](#lockrunning)|进入运行状态将锁定该控件。 ATL 实现返回`S_OK`。|  
|[IRunnableObjectImpl::Run](#run)|强制控件运行。 ATL 实现返回`S_OK`。|  
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|该值指示控件嵌入。 ATL 实现返回`S_OK`。|  
  
## <a name="remarks"></a>备注  
 [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783)接口使一个容器，以确定控件是否正在运行，强制其运行，或将其锁定进入运行状态。 类`IRunnableObjectImpl`提供此接口的默认实现，并实现**IUnknown**中调试设备信息发送给转储生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IRunnableObject`  
  
 `IRunnableObjectImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass  
 返回正在运行的控件的 CLSID。  
  
```
HRESULT GetRunningClass(LPCLSID lpClsid);
```  
  
### <a name="return-value"></a>返回值  
 ATL 实现集\* *lpClsid*到`GUID_NULL`，并返回**E_UNEXPECTED**。  
  
### <a name="remarks"></a>备注  
 请参阅[IRunnableObject::GetRunningClass](http://msdn.microsoft.com/library/windows/desktop/ms693734)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="isrunning"></a>IRunnableObjectImpl::IsRunning  
 确定控件是否正在运行。  
  
```
virtual BOOL IsRunning();
```  
  
### <a name="return-value"></a>返回值  
 ATL 实现返回**TRUE**。  
  
### <a name="remarks"></a>备注  
 请参阅[IRunnableObject::IsRunning](http://msdn.microsoft.com/library/windows/desktop/ms678496)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="lockrunning"></a>IRunnableObjectImpl::LockRunning  
 进入运行状态将锁定该控件。  
  
```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```  
  
### <a name="return-value"></a>返回值  
 ATL 实现返回`S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IRunnableObject::LockRunning](http://msdn.microsoft.com/library/windows/desktop/ms693361)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="run"></a>IRunnableObjectImpl::Run  
 强制控件运行。  
  
```
HRESULT Run(LPBINDCTX lpbc);
```  
  
### <a name="return-value"></a>返回值  
 ATL 实现返回`S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IRunnableObject::Run](http://msdn.microsoft.com/library/windows/desktop/ms694517)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setcontainedobject"></a>IRunnableObjectImpl::SetContainedObject  
 该值指示控件嵌入。  
  
```
HRESULT SetContainedObject(BOOL fContained);
```  
  
### <a name="return-value"></a>返回值  
 ATL 实现返回`S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IRunnableObject::SetContainedObject](http://msdn.microsoft.com/library/windows/desktop/ms693710)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [类概述](../../atl/atl-class-overview.md)

