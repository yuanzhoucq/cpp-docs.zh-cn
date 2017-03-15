---
title: "CAtlAutoThreadModuleT 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CAtlAutoThreadModuleT
- ATL::CAtlAutoThreadModuleT
- CAtlAutoThreadModuleT
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
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
ms.openlocfilehash: 86b35f0a6a3ab43c170ee710838ec9ba0e2fc5b0
ms.lasthandoff: 02/24/2017

---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT 类
此类提供用于实现线程池、 单元模型的 COM 服务器的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, 
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 一个类，该类将实现 COM 服务器。  
  
 `ThreadAllocator`  
 管理线程选择类。 默认值是[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
 `dwWait`  
 以毫秒为单位指定超时间隔。 默认值为 INFINITE，这意味着该方法的超时间隔永远不会经历。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|此静态函数动态计算并返回最大对于 EXE 模块，基于处理器的数量的线程数。|  
  
## <a name="remarks"></a>备注  
 此类[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)派生自`CAtlAutoThreadModuleT`为了实现线程池、 单元模型的 COM 服务器。 它将替换已过时的类别[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
> [!NOTE]
>  此类不应在一个 DLL，默认值为`dwWait`无限值将导致死锁时将在卸载 DLL。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlAutoThreadModule`  
  
 `CAtlAutoThreadModuleT`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="a-namegetdefaultthreadsa--catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads  
 此静态函数动态计算并返回最大对于 EXE 模块，基于处理器的数量的线程数。  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>返回值  
 要在 EXE 模块中创建的线程数。  
  
### <a name="remarks"></a>备注  
 如果你想要用另一种方法来计算的线程数，重写此方法。 默认情况下，线程数取决于处理器的数目。  
  
## <a name="see-also"></a>另请参阅  
 [IAtlAutoThreadModule 类](../../atl/reference/iatlautothreadmodule-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [IAtlAutoThreadModule 类](../../atl/reference/iatlautothreadmodule-class.md)   
 [Module 类](../../atl/atl-module-classes.md)

