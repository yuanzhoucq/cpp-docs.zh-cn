---
title: "critical_section 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::critical_section
dev_langs:
- C++
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
caps.latest.revision: 23
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 20a150c1aedbd9d78c84187bf29e6284a248fbc7
ms.lasthandoff: 02/24/2017

---
# <a name="criticalsection-class"></a>critical_section 类
明确感知并发运行时的不可重入互斥。  
  
## <a name="syntax"></a>语法  
  
```
class critical_section;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|`native_handle_type`|对 `critical_section` 对象的引用。|  
  
### <a name="public-classes"></a>公共类  
  
|名称|说明|  
|----------|-----------------|  
|[critical_section:: scoped_lock 类](#critical_section__scoped_lock_class)|有关的异常安全 RAII 包装`critical_section`对象。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[critical_section 构造函数](#ctor)|构造一个新的关键部分。|  
|[~ critical_section 析构函数](#dtor)|销毁临界区。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[lock 方法](#lock)|获取此临界区。|  
|[native_handle 方法](#native_handle)|返回的平台特定本机句柄，如果存在。|  
|[try_lock 方法](#try_lock)|尝试获取锁，而无需阻止。|  
|[try_lock_for 方法](#try_lock_for)|尝试在不将锁阻塞特定毫秒数的情况下获取锁。|  
|[unlock 方法](#unlock)|解除锁定关键节。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `critical_section`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namectora-criticalsection"></a><a name="ctor"></a>critical_section 

 构造一个新的关键部分。  
  
```
critical_section();
```  
  
##  <a name="a-namedtora-criticalsection"></a><a name="dtor"></a>~ critical_section 

 销毁临界区。  
  
```
~critical_section();
```  
  
### <a name="remarks"></a>备注  
 预计在析构函数运行时不再持有锁。 允许关键节锁析构仍保留会导致未定义的行为。  
  
##  <a name="a-namelocka-lock"></a><a name="lock"></a>锁 

 获取此临界区。  
  
```
void lock();
```  
  
### <a name="remarks"></a>备注  
 通常是更安全，以利用[scoped_lock](#critical_section__scoped_lock_class)构造来获取和释放`critical_section`异常中的对象安全的方式。  
  
 如果通过调用上下文中，已持有此锁[improper_lock](improper-lock-class.md)将会引发异常。  
  
##  <a name="a-namenativehandlea-nativehandle"></a><a name="native_handle"></a>native_handle 

 返回的平台特定本机句柄，如果存在。  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>返回值  
 对关键部分的引用。  
  
### <a name="remarks"></a>备注  
 一个`critical_section`对象不是与平台特定本机句柄关联的 Windows 操作系统。 该方法只是返回指向对象自身的引用。  
  
##  <a name="a-namecriticalsectionscopedlockclassa--criticalsectionscopedlock-class"></a><a name="critical_section__scoped_lock_class"></a>critical_section:: scoped_lock 类  
 有关的异常安全 RAII 包装`critical_section`对象。  
  
```
class scoped_lock;
```  
  
##  <a name="a-namecriticalsectionscopedlockctora-scopedlockscopedlock"></a><a name="critical_section__scoped_lock_ctor"></a>scoped_lock::scoped_lock 

 构造`scoped_lock`对象，并获取`critical_section`传入的对象`_Critical_section`参数。 如果由另一个线程持有关键节，此调用将阻塞。  
  
```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```  
  
### <a name="parameters"></a>参数  
 `_Critical_section`  
 若要锁定关键节。  
  
##  <a name="a-namecriticalsectionscopedlockdtora-scopedlockscopedlock"></a><a name="critical_section__scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock 

 销毁`scoped_lock`对象并释放关键节提供在其构造函数。  
  
```
~scoped_lock();
```  
  
##  <a name="a-nametrylocka-trylock"></a><a name="try_lock"></a>try_lock 

 尝试获取锁，而无需阻止。  
  
```
bool try_lock();
```  
  
### <a name="return-value"></a>返回值  
 如果已获取锁，则这`true`; 否则为值`false`。  
  
##  <a name="a-nametrylockfora-trylockfor"></a><a name="try_lock_for"></a>try_lock_for 

 尝试在不将锁阻塞特定毫秒数的情况下获取锁。  
  
```
bool try_lock_for(unsigned int _Timeout);
```  
  
### <a name="parameters"></a>参数  
 `_Timeout`  
 超时前要等待的毫秒数。  
  
### <a name="return-value"></a>返回值  
 如果已获取锁，则这`true`; 否则为值`false`。  
  
##  <a name="a-nameunlocka-unlock"></a><a name="unlock"></a>解除锁定 

 解除锁定关键节。  
  
```
void unlock();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [reader_writer_lock 类](reader-writer-lock-class.md)

