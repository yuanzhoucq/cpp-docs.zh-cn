---
title: "CComApartment 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
dev_langs:
- C++
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3fecd77e93c0c51a37d7363e6ec1472d157d6d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomapartment-class"></a>CComApartment 类
此类提供用于管理线程放入池中 EXE 模块中的房间的支持。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CComApartment
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComApartment::CComApartment](#ccomapartment)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComApartment::Apartment](#apartment)|将标记线程的起始地址。|  
|[CComApartment::GetLockCount](#getlockcount)|返回的线程的当前锁计数。|  
|[CComApartment::Lock](#lock)|线程的锁计数递增 1。|  
|[CComApartment::Unlock](#unlock)|递减线程的锁计数。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComApartment::m_dwThreadID](#m_dwthreadid)|包含线程的标识符。|  
|[CComApartment::m_hThread](#m_hthread)|包含线程的句柄。|  
|[CComApartment::m_nLockCnt](#m_nlockcnt)|包含线程的当前锁计数。|  
  
## <a name="remarks"></a>备注  
 `CComApartment`由[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)管理线程放入池中 EXE 模块中的某个单元。 `CComApartment`提供在一个线程上计数递增和递减锁的方法。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
##  <a name="apartment"></a>CComApartment::Apartment  
 将标记线程的起始地址。  
  
```
DWORD Apartment();
```  
  
### <a name="return-value"></a>返回值  
 始终为 0。  
  
### <a name="remarks"></a>备注  
 自动设置期间[CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init)。  
  
##  <a name="ccomapartment"></a>CComApartment::CComApartment  
 构造函数。  
  
```
CComApartment();
```  
  
### <a name="remarks"></a>备注  
 初始化`CComApartment`数据成员[m_nLockCnt](#m_nlockcnt)和[m_hThread](#m_hthread)。  
  
##  <a name="getlockcount"></a>CComApartment::GetLockCount  
 返回的线程的当前锁计数。  
  
```
LONG GetLockCount();
```  
  
### <a name="return-value"></a>返回值  
 线程锁上的锁计数。  
  
##  <a name="lock"></a>CComApartment::Lock  
 线程的锁计数递增 1。  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断或测试。  
  
### <a name="remarks"></a>备注  
 由调用[CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)。  
  
 在线程上的锁计数用于统计目的。  
  
##  <a name="m_dwthreadid"></a>CComApartment::m_dwThreadID  
 包含线程的标识符。  
  
```
DWORD m_dwThreadID;
```  
  
##  <a name="m_hthread"></a>CComApartment::m_hThread  
 包含线程的句柄。  
  
```
HANDLE m_hThread;
```  
  
##  <a name="m_nlockcnt"></a>CComApartment::m_nLockCnt  
 包含线程的当前锁计数。  
  
```
LONG m_nLockCnt;
```  
  
##  <a name="unlock"></a>CComApartment::Unlock  
 递减线程的锁计数。  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>返回值  
 一个值，可能是用于诊断或测试。  
  
### <a name="remarks"></a>备注  
 由调用[CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock)。  
  
 在线程上的锁计数用于统计目的。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
