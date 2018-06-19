---
title: CComAutoDeleteCriticalSection 类 |Microsoft 文档
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
ms.openlocfilehash: c5153520b5a5648f8352465031264c223ffd97c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360059"
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection 类
此类提供用于获取和释放的关键部分对象所有权的方法。  
  
## <a name="syntax"></a>语法  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>备注  
 `CComAutoDeleteCriticalSection` 派生自类[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)。 但是，`CComAutoDeleteCriticalSection`重写[术语](ccomsafedeletecriticalsection-class.md#term)方法`private`访问，这会强制内部内存清理，以仅当此类的实例超出范围或显式删除从内存时才发生。  

  
 此类引入了通过其基本类的任何其他方法。 请参阅[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)和[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)有关关键部分帮助程序类的详细信息。  
  
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
