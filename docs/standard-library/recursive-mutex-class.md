---
title: "recursive_mutex 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::recursive_mutex
dev_langs:
- C++
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
caps.latest.revision: 9
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: c82c8302be5d3e01de90adda2049a022100b8443
ms.lasthandoff: 02/24/2017

---
# <a name="recursivemutex-class"></a>recursive_mutex 类
表示互斥体类型。 与 [mutex](../standard-library/mutex-class-stl.md) 类相反，为已锁定的对象调用锁定方法的行为是有明确定义的。  
  
## <a name="syntax"></a>语法  
  
```
class recursive_mutex;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[recursive_mutex 构造函数](#recursive_mutex__recursive_mutex_constructor)|构造 `recursive_mutex` 对象。|  
|[~recursive_mutex 析构函数](#recursive_mutex___dtorrecursive_mutex_destructor)|释放由 `recursive_mutex` 对象使用的任何资源。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[lock](#recursive_mutex__lock_method)|阻止调用线程，直到线程获取 mutex 的所有权。|  
|[try_lock](#recursive_mutex__try_lock_method)|在不阻止的情况下尝试获取 mutex 的所有权。|  
|[unlock](#recursive_mutex__unlock_method)|释放 mutex 的所有权。|  
  
## <a name="requirements"></a>要求  
 **标头：**mutex  
  
 **命名空间：** std  
  
##  <a name="a-namerecursivemutexlockmethoda--lock"></a><a name="recursive_mutex__lock_method"></a>lock  
 阻止调用线程，直到线程获取 `mutex` 的所有权。  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>备注  
 如果调用线程已拥有 `mutex`，则该方法将立即返回，同时上一锁定保持有效。  
  
##  <a name="a-namerecursivemutexrecursivemutexconstructora--recursivemutex"></a><a name="recursive_mutex__recursive_mutex_constructor"></a>recursive_mutex  
 构造未锁定的 `recursive_mutex` 对象。  
  
```cpp  
recursive_mutex();
```  
  
##  <a name="a-namerecursivemutexdtorrecursivemutexdestructora--recursivemutex"></a><a name="recursive_mutex___dtorrecursive_mutex_destructor"></a>~recursive_mutex  
 释放由该对象使用的所有资源。  
  
```cpp  
~recursive_mutex();
```  
  
### <a name="remarks"></a>备注  
 如果当析构函数运行时对象被锁定，则该行为不确定。  
  
##  <a name="a-namerecursivemutextrylockmethoda--trylock"></a><a name="recursive_mutex__try_lock_method"></a>try_lock  
 在不阻止的情况下尝试获取 `mutex` 的所有权。  
  
```cpp  
bool try_lock() noexcept;
```  
  
### <a name="return-value"></a>返回值  
 如果此方法成功获取 `mutex` 的所有权，或如果调用线程已拥有 `mutex`，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 如果调用线程已拥有 `mutex`，则该函数将立即返回 `true`，并且上一锁定一直保持有效。  
  
##  <a name="a-namerecursivemutexunlockmethoda--unlock"></a><a name="recursive_mutex__unlock_method"></a>unlock  
 释放 mutex 的所有权。  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>备注  
 仅当 `mutex` 的调用次数与在 `recursive_mutex` 对象上成功调用 [lock](#recursive_mutex__lock_method) 和 [try_lock](#recursive_mutex__try_lock_method) 的次数一样多时，此方法才释放其所有权。  
  
 如果调用的线程不拥有 `mutex`，则该行为不确定。  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




