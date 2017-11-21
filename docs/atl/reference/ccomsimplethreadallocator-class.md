---
title: "CComSimpleThreadAllocator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
dev_langs: C++
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 150abb28f84d31e1ef6785f9109844529f10276d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
 `CComSimpleThreadAllocator`管理对的线程选择[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。 `CComSimpleThreadAllocator::GetThread`只需循环访问每个线程，并返回序列中的下一个。  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
##  <a name="getthread"></a>CComSimpleThreadAllocator::GetThread  
 通过指定序列中的下一个线程中选择一个线程。  
  
```
int GetThread(CComApartment* /* pApt */, int nThreads);
```  
  
### <a name="parameters"></a>参数  
 `pApt`  
 不在 ATL 的默认实现中使用。  
  
 `nThreads`  
 最大 EXE 模块中的线程数。  
  
### <a name="return-value"></a>返回值  
 一个整数，介于零和 ( `nThreads` -1)。 标识一个 EXE 模块中的线程。  
  
### <a name="remarks"></a>备注  
 您可以重写`GetThread`可以提供所选内容的不同方法，或要使用的`pApt`参数。  
  
 `GetThread`由调用[CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance)。  
  
## <a name="see-also"></a>另请参阅  
 [CComApartment 类](../../atl/reference/ccomapartment-class.md)   
 [类概述](../../atl/atl-class-overview.md)
