---
title: "CComCritSecLock 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 71b9ab8b11adc946656c2192c2f0f06555ef1254
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcritseclock-class"></a>CComCritSecLock 类
此类提供用于锁定和解锁的关键部分对象的方法。  
  
## <a name="syntax"></a>语法  
  
```
template<class TLock> class CComCritSecLock
```  
  
#### <a name="parameters"></a>参数  
 *TLock*  
 要进行锁定和解锁的对象。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComCritSecLock::CComCritSecLock](#ctor)|构造函数。|  
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComCritSecLock::Lock](#lock)|调用此方法以锁定关键部分对象。|  
|[CComCritSecLock::Unlock](#unlock)|调用此方法以解除锁定关键部分对象。|  
  
## <a name="remarks"></a>备注  
 此类用于锁定和解锁对象更安全的方式比与[CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)或[CComAutoCriticalSection 类](../../atl/reference/ccomautocriticalsection-class.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="ctor"></a>CComCritSecLock::CComCritSecLock  
 构造函数。  
  
```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```  
  
### <a name="parameters"></a>参数  
 *cs*  
 关键部分对象。  
  
 `bInitialLock`  
 初始的锁定状态︰ **true**方式锁定。  
  
### <a name="remarks"></a>备注  
 初始化关键部分对象。  
  
##  <a name="dtor"></a>CComCritSecLock:: ~ CComCritSecLock  
 析构函数。  
  
```
~CComCritSecLock() throw();
```  
  
### <a name="remarks"></a>备注  
 解除锁定关键部分对象。  
  
##  <a name="lock"></a>CComCritSecLock::Lock  
 调用此方法以锁定关键部分对象。  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果对象成功锁定，则为 S_OK 返回或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 如果该对象已被锁定，则断言会错误在调试版本中。  
  
##  <a name="unlock"></a>CComCritSecLock::Unlock  
 调用此方法以解除锁定关键部分对象。  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>备注  
 如果该对象已被解锁，则断言会错误在调试版本中。  
  
## <a name="see-also"></a>另请参阅  
 [CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)   
 [CComAutoCriticalSection 类](../../atl/reference/ccomautocriticalsection-class.md)

