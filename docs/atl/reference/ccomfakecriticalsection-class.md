---
title: CComFakeCriticalSection 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a042e52439579cfb1b4145b1691f5a00128754c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358610"
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection 类
此类提供相同的方法为[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)但未提供关键部分。  
  
## <a name="syntax"></a>语法  
  
```
class CComFakeCriticalSection
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComFakeCriticalSection::Init](#init)|由于没有任何关键部分，则任何影响。|  
|[CComFakeCriticalSection::Lock](#lock)|由于没有任何关键部分，则任何影响。|  
|[CComFakeCriticalSection::Term](#term)|由于没有任何关键部分，则任何影响。|  
|[CComFakeCriticalSection::Unlock](#unlock)|由于没有任何关键部分，则任何影响。|  
  
## <a name="remarks"></a>备注  
 `CComFakeCriticalSection` 镜像中找到的方法[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。 但是，`CComFakeCriticalSection`不提供一个临界区; 因此，其方法不执行任何操作。  
  
 通常情况下，使用`CComFakeCriticalSection`通过`typedef`命名，为`AutoCriticalSection`或`CriticalSection`。 使用时[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，这两种`typedef`名称引用`CComFakeCriticalSection`。 使用时[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，它们引用[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)和`CComCriticalSection`分别。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcore.h  
  
##  <a name="init"></a>  CComFakeCriticalSection::Init  
 由于没有任何关键部分，则任何影响。  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回，则为 S_OK。  
  
##  <a name="lock"></a>  CComFakeCriticalSection::Lock  
 由于没有任何关键部分，则任何影响。  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回，则为 S_OK。  
  
##  <a name="term"></a>  CComFakeCriticalSection::Term  
 由于没有任何关键部分，则任何影响。  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回，则为 S_OK。  
  
##  <a name="unlock"></a>  CComFakeCriticalSection::Unlock  
 由于没有任何关键部分，则任何影响。  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回，则为 S_OK。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
