---
title: CComCriticalSection 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
dev_langs:
- C++
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25376aba3cfbade202d1cf95c2218e88713ac22a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359900"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection 类
此类提供用于获取和释放的关键部分对象所有权的方法。  
  
## <a name="syntax"></a>语法  
  
```
class CComCriticalSection
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComCriticalSection::Init](#init)|创建并初始化关键部分对象。|  
|[CComCriticalSection::Lock](#lock)|获取关键部分对象的所有权。|  
|[CComCriticalSection::Term](#term)|释放系统资源使用的关键部分对象。|  
|[CComCriticalSection::Unlock](#unlock)|释放的关键部分对象的所有权。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComCriticalSection::m_sec](#m_sec)|A **CRITICAL_SECTION**对象。|  
  
## <a name="remarks"></a>备注  
 `CComCriticalSection` 类似于类[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)，只不过你必须显式初始化，并释放关键部分。  
  
 通常情况下，使用`CComCriticalSection`通过`typedef`名称[CriticalSection](ccommultithreadmodel-class.md#criticalsection)。 此名称引用`CComCriticalSection`时[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)正在使用。  

  
 请参阅[CComCritSecLock 类](../../atl/reference/ccomcritseclock-class.md)提供了一种更安全的方法，使用此类调用比`Lock`和`Unlock`直接。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcore.h  
  
##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection  
 构造函数。  
  
```
CComCriticalSection() throw();
```  
  
### <a name="remarks"></a>备注  
 集[m_sec](#m_sec)为 NULL 的数据成员 **。**  
  
##  <a name="init"></a>  CComCriticalSection::Init  
 调用 Win32 函数[InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472)，其中初始化中包含的关键部分对象[m_sec](#m_sec)数据成员。  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功后， **E_OUTOFMEMORY**或**E_FAIL**失败。  
  
##  <a name="lock"></a>  CComCriticalSection::Lock  
 调用 Win32 函数[EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608)，哪些等待线程可以获得中包含的关键部分对象的所有权[m_sec](#m_sec)数据成员。  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功后， **E_OUTOFMEMORY**或**E_FAIL**失败。  
  
### <a name="remarks"></a>备注  
 首先必须使用对的调用初始化的关键部分对象[Init](#init)方法。 当受保护的代码已完成执行时，必须调用线程[解锁](#unlock)可释放的关键部分的所有权。  
  
##  <a name="m_sec"></a>  CComCriticalSection::m_sec  
 包含由所有关键部分对象`CComCriticalSection`方法。  
  
```
CRITICAL_SECTION m_sec;
```  
  
##  <a name="term"></a>  CComCriticalSection::Term  
 调用 Win32 函数[DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552)，以释放使用中包含的关键部分对象的所有资源[m_sec](#m_sec)数据成员。  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 一次`Term`已调用的重要部分不再可用于同步。  
  
##  <a name="unlock"></a>  CComCriticalSection::Unlock  
 调用 Win32 函数[LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169)，其中释放中包含的关键部分对象的所有权[m_sec](#m_sec)数据成员。  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 若要首先获取所有权，线程必须调用[锁](#lock)方法。 每次调用`Lock`需要相应地调用`Unlock`可释放的关键部分的所有权。  
  
## <a name="see-also"></a>请参阅  
 [CComFakeCriticalSection 类](../../atl/reference/ccomfakecriticalsection-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [CComCritSecLock 类](../../atl/reference/ccomcritseclock-class.md)
