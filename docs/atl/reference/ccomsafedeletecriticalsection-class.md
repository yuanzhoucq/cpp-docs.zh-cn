---
title: "CComSafeDeleteCriticalSection 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
dev_langs:
- C++
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
caps.latest.revision: 18
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 511627de9d4f6411c508dd78a237cf546e2493de
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection 类
此类提供用于获取和释放关键节对象的所有权的方法。  
  
## <a name="syntax"></a>语法  
  
```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|构造函数。|  
|[CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::Init](#init)|创建并初始化关键部分对象。|  
|[CComSafeDeleteCriticalSection::Lock](#lock)|获取关键部分对象的所有权。|  
|[CComSafeDeleteCriticalSection::Term](#term)|释放系统资源使用的关键部分对象。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_bInitialized](#m_binitialized)|标志是否内部**CRITICAL_SECTION**初始化对象。|  
  
## <a name="remarks"></a>备注  
 `CComSafeDeleteCriticalSection`派生自类[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。 但是，`CComSafeDeleteCriticalSection`通过提供其他安全机制[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。  
  
 实例时`CComSafeDeleteCriticalSection`号超出范围或显式从内存中删除，基础的关键部分对象将自动清理是否仍然有效。 此外， [CComSafeDeleteCriticalSection::Term](#term)方法将正常退出，如果基础的关键部分对象尚未分配或已从内存释放。  
  
 请参阅[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)的临界区的帮助器类的详细信息。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComSafeDeleteCriticalSection`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcore.h  
  
##  <a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection  
 构造函数。  
  
```
CComSafeDeleteCriticalSection();
```  
  
### <a name="remarks"></a>备注  
 集[m_bInitialized](#m_binitialized)数据成员与**false**。  
  
##  <a name="dtor"></a>CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection  
 析构函数。  
  
```
~CComSafeDeleteCriticalSection() throw();
```  
  
### <a name="remarks"></a>备注  
 释放内部**CRITICAL_SECTION**对象从内存中，如果[m_bInitialized](#m_binitialized)数据成员设置为**true**。  
  
##  <a name="init"></a>CComSafeDeleteCriticalSection::Init  
 调用基类实现[Init](/visualstudio/debugger/init) ，并设置[m_bInitialized](#m_binitialized)到**true**如果操作成功。  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的结果[CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init)。  
  
##  <a name="lock"></a>CComSafeDeleteCriticalSection::Lock  
调用基类实现[锁](ccomcriticalsection-class.md#lock)。  

  
```
HRESULT Lock();
```  
  
### <a name="return-value"></a>返回值  
 返回的结果[CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock)。  
  
### <a name="remarks"></a>备注  
 此方法假定[m_bInitialized](#m_binitialized)数据成员设置为**true**在入口。 如果不满足此 condidtion，在调试版本中将生成断言。  
  
 有关在行为上的函数的详细信息，请参阅[CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock)。  
  
##  <a name="m_binitialized"></a>CComSafeDeleteCriticalSection::m_bInitialized  
 标志是否内部**CRITICAL_SECTION**初始化对象。  
  
```
bool m_bInitialized;
```  
  
### <a name="remarks"></a>备注  
 **M_bInitialized**数据成员用于跟踪的基础有效性**CRITICAL_SECTION**与关联对象[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)类。 基础**CRITICAL_SECTION**对象不会尝试从内存释放，如果此标志未设置为**true**。  
  
##  <a name="term"></a>CComSafeDeleteCriticalSection::Term  
 调用基类实现[CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term)如果内部**CRITICAL_SECTION**对象是否有效。  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的结果[CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term)，或**，则为 S_OK**如果[m_bInitialized](#m_binitialized)已设置为**false**在入口。  
  
### <a name="remarks"></a>备注  
 可以安全地调用此方法，即使内部**CRITICAL_SECTION**对象无效。 此类的析构函数将调用此方法如果[m_bInitialized](#m_binitialized)数据成员设置为**true**。  
  
## <a name="see-also"></a>另请参阅  
 [CComCriticalSection 类](../../atl/reference/ccomcriticalsection-class.md)   
 [类概述](../../atl/atl-class-overview.md)

