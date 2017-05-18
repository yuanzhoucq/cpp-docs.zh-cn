---
title: "reader_writer_lock 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 21
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: b5107923baa7d22e6a98c6617a22a883c4d84125
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

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
|[reader_writer_lock:: scoped_lock 类](#scoped_lock_class)|异常安全 RAII 包装可用于获取`reader_writer_lock`作为编写器锁的对象。|  
|[reader_writer_lock:: scoped_lock_read 类](#scoped_lock_read_class)|异常安全 RAII 包装可用于获取`reader_writer_lock`锁定对象用作一个读取器。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[reader_writer_lock](#ctor)|构造一个新`reader_writer_lock`对象。|  
|[~ reader_writer_lock 析构函数](#dtor)|销毁`reader_writer_lock`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[lock](#lock)|获取读取器 / 编写器锁，用作一个编写器。|  
|[lock_read](#lock_read)|获取读取器 / 编写器锁，用作一个读取器。 如果有编写器，活动的读取器必须等待，直到它们完成。 读取器只需注册感兴趣的锁，并等待编写器将其释放。|  
|[try_lock](#try_lock)|尝试获取作为编写器读取器 / 编写器锁，而无需阻止。|  
|[try_lock_read](#try_lock_read)|尝试获取为读取器读取器 / 编写器锁，而不会阻止。|  
|[unlock](#unlock)|解除锁定根据它、 读取器或编写器锁定的读取器 / 编写器锁。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `reader_writer_lock`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="lock"></a>锁 

 获取读取器 / 编写器锁，用作一个编写器。  
  
```
void lock();
```  
  
### <a name="remarks"></a>备注  
 通常是更安全，以利用[scoped_lock](#scoped_lock_class)构造来获取和释放`reader_writer_lock`引发异常的撰稿人对象安全的方式。  
  
 在编写器尝试获取锁后，在编写器成功获取和释放该锁之前任何将来的读取器都将阻塞。 此锁定偏爱编写器且不会停止在编写器连续负载下的读取器。  
  
 编写器链接在一起，以便编写器退出锁释放行中的下一步编写器。  
  
 如果通过调用上下文中，已持有此锁[improper_lock](improper-lock-class.md)将会引发异常。  
  
##  <a name="lock_read"></a>lock_read 

 获取读取器 / 编写器锁，用作一个读取器。 如果有编写器，活动的读取器必须等待，直到它们完成。 读取器只需注册感兴趣的锁，并等待编写器将其释放。  
  
```
void lock_read();
```  
  
### <a name="remarks"></a>备注  
 通常是更安全，以利用[scoped_lock_read](#scoped_lock_read_class)构造来获取和释放`reader_writer_lock`对象作为一个读取器引发异常安全的方式。  
  
 如果有正在等待锁的编写器，则读取器将等待，直到在行中的所有编写器已获取并释放该锁。 此锁定偏爱编写器且不会停止在编写器连续负载下的读取器。  
  
##  <a name="ctor"></a>reader_writer_lock 

 构造一个新`reader_writer_lock`对象。  
  
```
reader_writer_lock();
```  
  
##  <a name="dtor"></a>~ reader_writer_lock 

 销毁`reader_writer_lock`对象。  
  
```
~reader_writer_lock();
```  
  
### <a name="remarks"></a>备注  
 预计在析构函数运行时不再持有锁。 允许读取器编写器锁与锁定析构仍保留会导致未定义的行为。  
  
##  <a name="scoped_lock_class"></a>reader_writer_lock:: scoped_lock 类  
 异常安全 RAII 包装可用于获取`reader_writer_lock`作为编写器锁的对象。  
  
```
class scoped_lock;
``` 
## <a name="scoped_lock_ctor"></a>scoped_lock::scoped_lock 

构造`scoped_lock`对象，并获取`reader_writer_lock`传入的对象`_Reader_writer_lock`作为编写器的参数。 如果由另一个线程持有此锁，则此调用将阻塞。  
  
  
```
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>参数  
 `_Reader_writer_lock`  
 `reader_writer_lock`对象获取的撰稿人。  
  
## <a name="scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock 

销毁`reader_writer_lock`对象并释放其构造函数中提供的锁。   

```
~scoped_lock();
```  
  
##  <a name="scoped_lock_read_class"></a>reader_writer_lock:: scoped_lock_read 类  
 异常安全 RAII 包装可用于获取`reader_writer_lock`锁定对象用作一个读取器。  
  
```
class scoped_lock_read;
```  
  
##  <a name="try_lock"></a>try_lock 

 尝试获取作为编写器读取器 / 编写器锁，而无需阻止。  

## <a name="scoped_lock_read_ctor"></a>scoped_lock_read::scoped_lock_read 

构造`scoped_lock_read`对象，并获取`reader_writer_lock`传入的对象`_Reader_writer_lock`参数作为一个读取器。 如果由作为编写器的另一个线程持有锁或有挂起的编写器，此调用将阻塞。  
  
```
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>参数  
 `_Reader_writer_lock`  
 `reader_writer_lock`要获取作为读取器对象。  
  
## <a name="a-namescopedlockreaddtor--readerwriterlockscopedlockreadscopedlockread-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock:: scoped_lock_read:: ~ scoped_lock_read 析构函数
销毁`scoped_lock_read`对象并释放其构造函数中提供的锁。  

```
~scoped_lock_read();
```  
  
## <a name="try_lock"></a>try_lock 

```
bool try_lock();
```  
  
### <a name="return-value"></a>返回值  
 如果已获取锁，则这`true`; 否则为值`false`。  
  
##  <a name="try_lock_read"></a>try_lock_read 

 尝试获取为读取器读取器 / 编写器锁，而不会阻止。  
  
```
bool try_lock_read();
```  
  
### <a name="return-value"></a>返回值  
 如果已获取锁，则这`true`; 否则为值`false`。  
  
##  <a name="unlock"></a>解除锁定 

 解除锁定根据它、 读取器或编写器锁定的读取器 / 编写器锁。  
  
```
void unlock();
```  
  
### <a name="remarks"></a>备注  
 如果有正在等待锁的编写器，释放锁会始终转到按 FIFO 顺序的下一步编写器。 此锁定偏爱编写器且不会停止在编写器连续负载下的读取器。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [critical_section 类](critical-section-class.md)

