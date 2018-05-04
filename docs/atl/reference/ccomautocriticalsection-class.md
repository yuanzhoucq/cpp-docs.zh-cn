---
title: CComAutoCriticalSection 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae0c3cd1d00ce83a4e952d60a978663bfa76f814
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection 类
`CComAutoCriticalSection` 提供用于获取和释放的关键部分对象所有权方法。  
  
## <a name="syntax"></a>语法  
  
```
class CComAutoCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|构造函数。|  
|[CComAutoCriticalSection:: ~ CComAutoCriticalSection](#dtor)|析构函数。|  
  
## <a name="remarks"></a>备注  
 `CComAutoCriticalSection` 类似于类[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)，除`CComAutoCriticalSection`自动初始化构造函数中的关键部分对象。  
  
 通常情况下，使用`CComAutoCriticalSection`通过`typedef`名称[AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection)。 此名称引用`CComAutoCriticalSection`时[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)正在使用。  

  
 `Init`和`Term`方法从[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)时使用此类不可用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComAutoCriticalSection`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcore.h  
  
##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection  
 构造函数。  
  
```
CComAutoCriticalSection();
```  
  
### <a name="remarks"></a>备注  
 调用 Win32 函数[InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472)，其中初始化关键部分对象。  
  
##  <a name="dtor"></a>  CComAutoCriticalSection:: ~ CComAutoCriticalSection  
 析构函数。  
  
```
~CComAutoCriticalSection() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数调用[DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552)，以释放使用的关键部分对象的所有系统资源。  
  
## <a name="see-also"></a>请参阅  
 [CComFakeCriticalSection 类](../../atl/reference/ccomfakecriticalsection-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)
