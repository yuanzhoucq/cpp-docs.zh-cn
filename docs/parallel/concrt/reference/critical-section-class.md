---
title: critical_section 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
dev_langs:
- C++
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0287c74155e7b4fe827bb015b43cfca3384f3b1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="criticalsection-class"></a>critical_section 类
明确感知并发运行时的不可重入互斥。  
  
## <a name="syntax"></a>语法  
  
```
class critical_section;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`native_handle_type`|对 `critical_section` 对象的引用。|  
  
### <a name="public-classes"></a>公共类  
  
|名称|描述|  
|----------|-----------------|  
|[critical_section:: scoped_lock 类](#critical_section__scoped_lock_class)|异常安全 RAII 包装器`critical_section`对象。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[critical_section](#ctor)|构造新的关键部分。|  
|[~ critical_section 析构函数](#dtor)|销毁关键部分。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[lock](#lock)|获取此临界区。|  
|[native_handle](#native_handle)|返回的平台特定本机句柄，如果存在。|  
|[try_lock](#try_lock)|尝试获取锁，而不阻止。|  
|[try_lock_for](#try_lock_for)|尝试在不将锁阻塞特定毫秒数的情况下获取锁。|  
|[unlock](#unlock)|解除锁定关键部分。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `critical_section`  
  
## <a name="requirements"></a>要求  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a> critical_section 

 构造新的关键部分。  
  
```
critical_section();
```  
  
##  <a name="dtor"></a> ~critical_section 

 销毁关键部分。  
  
```
~critical_section();
```  
  
### <a name="remarks"></a>备注  
 应析构函数运行时不再持有锁。 允许要与锁定析构的关键部分仍保留会导致未定义的行为。  
  
##  <a name="lock"></a> 锁 

 获取此临界区。  
  
```
void lock();
```  
  
### <a name="remarks"></a>备注  
 它通常是更安全利用[scoped_lock](#critical_section__scoped_lock_class)构造来获取和发布`critical_section`中异常对象安全的方式。  
  
 如果锁已经被调用的上下文中，保留[improper_lock](improper-lock-class.md)将引发异常。  
  
##  <a name="native_handle"></a> native_handle 

 返回的平台特定本机句柄，如果存在。  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>返回值  
 对关键部分的引用。  
  
### <a name="remarks"></a>备注  
 A`critical_section`对象不是与平台特定本机句柄关联的 Windows 操作系统。 方法只需返回到对象本身的引用。  
  
##  <a name="critical_section__scoped_lock_class"></a>  critical_section:: scoped_lock 类  
 异常安全 RAII 包装器`critical_section`对象。  
  
```
class scoped_lock;
```  
  
##  <a name="critical_section__scoped_lock_ctor"></a> scoped_lock::scoped_lock 

 构造`scoped_lock`对象，并获取`critical_section`传入的对象`_Critical_section`参数。 如果关键部分由另一个线程，则此调用将阻塞。  
  
```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```  
  
### <a name="parameters"></a>参数  
 `_Critical_section`  
 要锁定的关键部分。  
  
##  <a name="critical_section__scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock 

 销毁`scoped_lock`对象并释放其构造函数中提供的关键部分。  
  
```
~scoped_lock();
```  
  
##  <a name="try_lock"></a> try_lock 

 尝试获取锁，而不阻止。  
  
```
bool try_lock();
```  
  
### <a name="return-value"></a>返回值  
 如果已获取锁，则这`true`; 否则为值`false`。  
  
##  <a name="try_lock_for"></a> try_lock_for 

 尝试在不将锁阻塞特定毫秒数的情况下获取锁。  
  
```
bool try_lock_for(unsigned int _Timeout);
```  
  
### <a name="parameters"></a>参数  
 `_Timeout`  
 超时前要等待的毫秒数。  
  
### <a name="return-value"></a>返回值  
 如果已获取锁，则这`true`; 否则为值`false`。  
  
##  <a name="unlock"></a> 解锁 

 解除锁定关键部分。  
  
```
void unlock();
```  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [reader_writer_lock 类](reader-writer-lock-class.md)
