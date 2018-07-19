---
title: CComAutoDeleteCriticalSection 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8b90afb9ae47ced33c331aef988489b567b1078b
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879897"
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection 类
此类提供方法用于获取并释放关键节对象的所有权。  
  
## <a name="syntax"></a>语法  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>备注  
 `CComAutoDeleteCriticalSection` 派生自类[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)。 但是，`CComAutoDeleteCriticalSection`重写[术语](ccomsafedeletecriticalsection-class.md#term)方法**专用**访问，这会强制执行仅在此类的实例会超出范围或显式删除从内部内存清理操作内存。  

  
 此类通过其基类引入了任何其他方法。 请参阅[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)并[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)的关键部分帮助程序类的详细信息。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcore.h  
  
## <a name="see-also"></a>请参阅  
 [CComSafeDeleteCriticalSection 类](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)   
 [类概述](../../atl/atl-class-overview.md)
