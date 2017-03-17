---
title: "CComFakeCriticalSection 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 2c1269288e03a8ac9f359dad9acf1a81ddbc84c2
ms.lasthandoff: 02/24/2017

---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection 类
此类提供与相同的方法[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)但未提供的关键部分。  
  
## <a name="syntax"></a>语法  
  
```
class CComFakeCriticalSection
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComFakeCriticalSection::Init](#init)|没有任何影响，因为没有关键节。|  
|[CComFakeCriticalSection::Lock](#lock)|没有任何影响，因为没有关键节。|  
|[CComFakeCriticalSection::Term](#term)|没有任何影响，因为没有关键节。|  
|[CComFakeCriticalSection::Unlock](#unlock)|没有任何影响，因为没有关键节。|  
  
## <a name="remarks"></a>备注  
 `CComFakeCriticalSection`镜像中找到的方法[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。 但是，`CComFakeCriticalSection`不提供关键的部分; 因此，其方法不执行任何操作。  
  
 通常，您可以使用`CComFakeCriticalSection`通过`typedef`命名，为`AutoCriticalSection`或`CriticalSection`。 当使用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，这两种`typedef`名称引用`CComFakeCriticalSection`。 当使用[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，它们引用[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)和`CComCriticalSection`分别。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcore.h  
  
##  <a name="init"></a>CComFakeCriticalSection::Init  
 没有任何影响，因为没有关键节。  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回，则为 S_OK。  
  
##  <a name="lock"></a>CComFakeCriticalSection::Lock  
 没有任何影响，因为没有关键节。  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回，则为 S_OK。  
  
##  <a name="term"></a>CComFakeCriticalSection::Term  
 没有任何影响，因为没有关键节。  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回，则为 S_OK。  
  
##  <a name="unlock"></a>CComFakeCriticalSection::Unlock  
 没有任何影响，因为没有关键节。  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回，则为 S_OK。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

