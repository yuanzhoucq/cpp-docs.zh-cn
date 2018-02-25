---
title: "reader_writer_lock 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
dev_langs:
- C++
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 75bea63c6e2f73ebd58434874758c4f20444958a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="readerwriterlock-class"></a>reader_writer_lock 类
具有仅限本地旋转的基于编写器首选队列的读取器-编写器锁。 锁授予对编写器的先进先出 (FIFO) 访问权限，并在出现编写器持续负载的情况下停止读取器。  
  
## <a name="syntax"></a>语法  
  
```
class reader_writer_lock;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-classes"></a>公共类  
  
|名称|描述|  
|----------|-----------------|  
|[reader_writer_lock:: scoped_lock 类](#scoped_lock_class)|异常安全 RAII 包装器可用于获取`reader_writer_lock`为编写器锁定对象。|  
|[reader_writer_lock:: scoped_lock_read 类](#scoped_lock_read_class)|异常安全 RAII 包装器可用于获取`reader_writer_lock`锁定对象用作一个读取器。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[reader_writer_lock](#ctor)|构造一个新`reader_writer_lock`对象。|  
|[~ reader_writer_lock 析构函数](#dtor)|销毁`reader_writer_lock`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[lock](#lock)|获取读取器 / 编写器锁，用作一个编写器。|  
|[lock_read](#lock_read)|获取读取器 / 编写器锁，用作一个读取器。 如果有编写器，活动的读取器必须等待，直到它们完成。 读取器只需注册感兴趣锁定并等待编写器释放它。|  
|[try_lock](#try_lock)|尝试获取读取器 / 编写器锁为编写器而不阻止。|  
|[try_lock_read](#try_lock_read)|尝试获取读取器 / 编写器锁为读取器不阻塞。|  
|[unlock](#unlock)|解除锁定，基于由谁锁定它、 读取器或编写器将读取器写线程锁。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `reader_writer_lock`  
  
## <a name="requirements"></a>惠?  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="lock"></a> 锁 

 获取读取器 / 编写器锁，用作一个编写器。  
  
```
void lock();
```  
  
### <a name="remarks"></a>备注  
 它通常是更安全利用[scoped_lock](#scoped_lock_class)构造来获取和发布`reader_writer_lock`对象引发异常的编写器作为安全的方式。  
  
 在编写器尝试获取锁后，在编写器成功获取和释放该锁之前任何将来的读取器都将阻塞。 此锁朝编写器偏离，并且可以阻止编写器持续负载下的读取器。  
  
 编写器被链接，以便编写器正在退出锁释放行中的下一步编写器。  
  
 如果锁已经被调用的上下文中，保留[improper_lock](improper-lock-class.md)将引发异常。  
  
##  <a name="lock_read"></a> lock_read 

 获取读取器 / 编写器锁，用作一个读取器。 如果有编写器，活动的读取器必须等待，直到它们完成。 读取器只需注册感兴趣锁定并等待编写器释放它。  
  
```
void lock_read();
```  
  
### <a name="remarks"></a>备注  
 它通常是更安全利用[scoped_lock_read](#scoped_lock_read_class)构造来获取和发布`reader_writer_lock`对象作为一个读取器引发异常安全的方式。  
  
 如果有正在等待锁的编写器，读取器将等待，直到在行中的所有编写器已获取并释放该锁。 此锁朝编写器偏离，并且可以阻止编写器持续负载下的读取器。  
  
##  <a name="ctor"></a> reader_writer_lock 

 构造一个新`reader_writer_lock`对象。  
  
```
reader_writer_lock();
```  
  
##  <a name="dtor"></a> ~reader_writer_lock 

 销毁`reader_writer_lock`对象。  
  
```
~reader_writer_lock();
```  
  
### <a name="remarks"></a>备注  
 应析构函数运行时不再持有锁。 允许读取器编写器锁与锁定析构仍保留会导致未定义的行为。  
  
##  <a name="scoped_lock_class">reader_writer_lock:: scoped_lock 类</a>  
 异常安全 RAII 包装器可用于获取`reader_writer_lock`为编写器锁定对象。  
  
```
class scoped_lock;
``` 
## <a name="scoped_lock_ctor"></a> scoped_lock::scoped_lock 

构造`scoped_lock`对象，并获取`reader_writer_lock`传入的对象`_Reader_writer_lock`为编写器的参数。 如果锁被保留由另一个线程，则此调用将阻塞。  
  
  
```
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>参数  
 `_Reader_writer_lock`  
 `reader_writer_lock`要获取为编写器对象。  
  
## <a name="scoped_lock_dtor"></a> scoped_lock::~scoped_lock 

销毁`reader_writer_lock`对象并释放其构造函数中提供的锁。   

```
~scoped_lock();
```  
  
##  <a name="scoped_lock_read_class">reader_writer_lock:: scoped_lock_read 类</a>  
 异常安全 RAII 包装器可用于获取`reader_writer_lock`锁定对象用作一个读取器。  
  
```
class scoped_lock_read;
```  
  
##  <a name="try_lock"></a> try_lock 

 尝试获取读取器 / 编写器锁为编写器而不阻止。  

## <a name="scoped_lock_read_ctor"></a> scoped_lock_read::scoped_lock_read 

构造`scoped_lock_read`对象，并获取`reader_writer_lock`传入的对象`_Reader_writer_lock`作为读取器的参数。 如果锁被保留由为编写器的另一个线程或有挂起的编写器，此调用将阻止。  
  
```
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>参数  
 `_Reader_writer_lock`  
 `reader_writer_lock`作为读取器获取的对象。  
  
## <a name="a-namescopedlockreaddtor--readerwriterlockscopedlockreadscopedlockread-destructor"></a><a name="scoped_lock_read_dtor">  reader_writer_lock:: scoped_lock_read:: ~ scoped_lock_read 析构函数
销毁`scoped_lock_read`对象并释放其构造函数中提供的锁。  

```
~scoped_lock_read();
```  
  
## <a name="try_lock"></a> try_lock 

```
bool try_lock();
```  
  
### <a name="return-value"></a>返回值  
 如果已获取锁，则这`true`; 否则为值`false`。  
  
##  <a name="try_lock_read"></a> try_lock_read 

 尝试获取读取器 / 编写器锁为读取器不阻塞。  
  
```
bool try_lock_read();
```  
  
### <a name="return-value"></a>返回值  
 如果已获取锁，则这`true`; 否则为值`false`。  
  
##  <a name="unlock"></a> 解锁 

 解除锁定，基于由谁锁定它、 读取器或编写器将读取器写线程锁。  
  
```
void unlock();
```  
  
### <a name="remarks"></a>备注  
 如果有正在等待锁的编写器，释放锁将始终转到按 FIFO 顺序的下一步编写器。 此锁朝编写器偏离，并且可以阻止编写器持续负载下的读取器。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [critical_section 类](critical-section-class.md)
