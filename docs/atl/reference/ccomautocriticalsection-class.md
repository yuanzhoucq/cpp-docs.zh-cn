---
title: "CComAutoCriticalSection 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
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
ms.openlocfilehash: 9f58a4cfd02af09a05b625a7e02b574b672adade
ms.lasthandoff: 02/24/2017

---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection 类
`CComAutoCriticalSection`提供用于获取和释放关键节对象所有权的方法。  
  
## <a name="syntax"></a>语法  
  
```
class CComAutoCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|构造函数。|  
|[CComAutoCriticalSection:: ~ CComAutoCriticalSection](#dtor)|析构函数。|  
  
## <a name="remarks"></a>备注  
 `CComAutoCriticalSection`类似于类[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)，除`CComAutoCriticalSection`自动初始化的构造函数中的关键部分对象。  
  
 通常，您可以使用`CComAutoCriticalSection`通过`typedef`名称[AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection)。 此名称引用`CComAutoCriticalSection`时[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)正在使用。  

  
 `Init`和`Term`方法从[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)时使用此类不可用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComAutoCriticalSection`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcore.h  
  
##  <a name="ccomautocriticalsection"></a>CComAutoCriticalSection::CComAutoCriticalSection  
 构造函数。  
  
```
CComAutoCriticalSection();
```  
  
### <a name="remarks"></a>备注  
 调用 Win32 函数[InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472)，其中初始化关键部分对象。  
  
##  <a name="dtor"></a>CComAutoCriticalSection:: ~ CComAutoCriticalSection  
 析构函数。  
  
```
~CComAutoCriticalSection() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数调用[DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552)，以释放使用的关键部分对象的所有系统资源。  
  
## <a name="see-also"></a>另请参阅  
 [CComFakeCriticalSection 类](../../atl/reference/ccomfakecriticalsection-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)

