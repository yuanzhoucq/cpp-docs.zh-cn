---
title: CAtlAutoThreadModuleT 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a54818b839f13ad9114274248cfdbfc74efa033a
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883068"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT 类
此类提供用于实现为在线程池的单元模型 COM 服务器的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, 
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```  
  
#### <a name="parameters"></a>参数  
 *T*  
 一个类，该类将实现 COM 服务器。  
  
 *ThreadAllocator*  
 管理线程选择类。 默认值是[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
 *dwWait*  
 指定的超时间隔，以毫秒为单位。 默认值为 INFINITE，这意味着该方法的超时间隔永远不会经历。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|此静态函数动态计算并返回最大为 EXE 模块，基于处理器的数量的线程数。|  
  
## <a name="remarks"></a>备注  
 该类[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)派生自`CAtlAutoThreadModuleT`才能实现为在线程池的单元模型 COM 服务器。 它取代了已过时的类别[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
> [!NOTE]
>  此类不应在一个 DLL，为默认*dwWait*卸载 DLL 时，无限的值将导致死锁。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlAutoThreadModule`  
  
 `CAtlAutoThreadModuleT`  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
##  <a name="getdefaultthreads"></a>  CAtlAutoThreadModuleT::GetDefaultThreads  
 此静态函数动态计算并返回最大为 EXE 模块，基于处理器的数量的线程数。  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>返回值  
 要在 EXE 模块中创建的线程数。  
  
### <a name="remarks"></a>备注  
 如果你想要使用不同的方法用于计算的线程数，重写此方法。 默认情况下，线程数取决于处理器数。  
  
## <a name="see-also"></a>请参阅  
 [IAtlAutoThreadModule 类](../../atl/reference/iatlautothreadmodule-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [IAtlAutoThreadModule 类](../../atl/reference/iatlautothreadmodule-class.md)   
 [Module 类](../../atl/atl-module-classes.md)
