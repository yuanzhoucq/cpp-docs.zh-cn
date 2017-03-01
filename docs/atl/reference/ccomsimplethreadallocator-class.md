---
title: "CComSimpleThreadAllocator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSimpleThreadAllocator
- ATL::CComSimpleThreadAllocator
- ATL.CComSimpleThreadAllocator
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
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
ms.openlocfilehash: 377e7f2fa6d8377d46e98b52e9c8f075b10956a8
ms.lasthandoff: 02/24/2017

---
# <a name="ccomsimplethreadallocator-class"></a>CComSimpleThreadAllocator 类
此类管理类的线程选择`CComAutoThreadModule`。  
  
## <a name="syntax"></a>语法  
  
```
class CComSimpleThreadAllocator
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComSimpleThreadAllocator::GetThread](#getthread)|选择一个线程。|  
  
## <a name="remarks"></a>备注  
 `CComSimpleThreadAllocator`管理的线程选择[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。 `CComSimpleThreadAllocator::GetThread`只需循环访问每个线程，并返回序列中的下一个。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="a-namegetthreada--ccomsimplethreadallocatorgetthread"></a><a name="getthread"></a>CComSimpleThreadAllocator::GetThread  
 选择一个线程通过指定序列中的下一个线程。  
  
```
int GetThread(CComApartment* /* pApt */, int nThreads);
```  
  
### <a name="parameters"></a>参数  
 `pApt`  
 ATL 的默认实现中不使用。  
  
 `nThreads`  
 最大 EXE 模块中的线程数。  
  
### <a name="return-value"></a>返回值  
 一个整数，介于零和 ( `nThreads` – 1)。 标识一个 EXE 模块中的线程。  
  
### <a name="remarks"></a>备注  
 您可以重写`GetThread`提供不同的方法所选内容，或者使利用`pApt`参数。  
  
 `GetThread`由调用[CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance)。  
  
## <a name="see-also"></a>另请参阅  
 [CComApartment 类](../../atl/reference/ccomapartment-class.md)   
 [类概述](../../atl/atl-class-overview.md)

