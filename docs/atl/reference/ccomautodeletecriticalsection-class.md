---
title: "CComAutoDeleteCriticalSection 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0a0c5fdd45e819105a3f47e98c02bb5ad3d51be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection 类
此类提供用于获取和释放的关键部分对象所有权的方法。  
  
## <a name="syntax"></a>语法  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>备注  
 `CComAutoDeleteCriticalSection`派生自类[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)。 但是，`CComAutoDeleteCriticalSection`重写[术语](ccomsafedeletecriticalsection-class.md#term)方法`private`访问，这会强制内部内存清理，以仅当此类的实例超出范围或显式删除从内存时才发生。  

  
 此类引入了通过其基本类的任何其他方法。 请参阅[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)和[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)有关关键部分帮助程序类的详细信息。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcore.h  
  
## <a name="see-also"></a>请参阅  
 [CComSafeDeleteCriticalSection 类](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)   
 [类概述](../../atl/atl-class-overview.md)
