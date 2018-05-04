---
title: CComCritSecLock 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b6eb7a8e6df16134573b55a7c9666befe4e4a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock 类
此类提供用于锁定和解锁的关键部分对象的方法。  
  
## <a name="syntax"></a>语法  
  
```
template<class TLock> class CComCritSecLock
```  
  
#### <a name="parameters"></a>参数  
 *TLock*  
 要锁定和解锁的对象。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComCritSecLock::CComCritSecLock](#ctor)|构造函数。|  
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComCritSecLock::Lock](#lock)|调用此方法以锁定关键部分对象。|  
|[CComCritSecLock::Unlock](#unlock)|调用此方法以解锁关键部分对象。|  
  
## <a name="remarks"></a>备注  
 此类用于锁定和解锁对象与使用更安全的方式[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)或[CComAutoCriticalSection 类](../../atl/reference/ccomautocriticalsection-class.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
##  <a name="ctor"></a>  CComCritSecLock::CComCritSecLock  
 构造函数。  
  
```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```  
  
### <a name="parameters"></a>参数  
 *cs*  
 关键部分对象中。  
  
 `bInitialLock`  
 初始的锁定状态： **true**方式锁定。  
  
### <a name="remarks"></a>备注  
 初始化关键部分对象。  
  
##  <a name="dtor"></a>  CComCritSecLock:: ~ CComCritSecLock  
 析构函数。  
  
```
~CComCritSecLock() throw();
```  
  
### <a name="remarks"></a>备注  
 解除锁定关键部分对象。  
  
##  <a name="lock"></a>  CComCritSecLock::Lock  
 调用此方法以锁定关键部分对象。  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果对象已成功锁定，则为 S_OK 返回或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 如果对象已被锁定，在调试版本中将会出错断言。  
  
##  <a name="unlock"></a>  CComCritSecLock::Unlock  
 调用此方法以解锁关键部分对象。  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>备注  
 如果该对象已解锁，断言错误将在调试版本中发生。  
  
## <a name="see-also"></a>请参阅  
 [CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)   
 [CComAutoCriticalSection 类](../../atl/reference/ccomautocriticalsection-class.md)
