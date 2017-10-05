---
title: "&lt;mutex&gt; 函数和变量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::adopt_lock
- mutex/std::call_once
- mutex/std::defer_lock
- mutex/std::lock
- mutex/std::try_to_lock
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
caps.latest.revision: 11
manager: ghogen
helpviewer_keywords:
- std::adopt_lock [C++]
- std::call_once [C++]
- std::defer_lock [C++]
- std::lock [C++]
- std::try_to_lock [C++]
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: a81d134a4fb49f9123dbed5b4146976d5c676379
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;mutex&gt; 函数和变量
||||  
|-|-|-|  
|[adopt_lock](#adopt_lock)|[call_once](#call_once)|[defer_lock](#defer_lock)|  
|[lock](#lock)|[try_to_lock](#try_to_lock)|  
  
##  <a name="adopt_lock"></a>adopt_lock 变量  
 表示可传递给 [lock_guard](../standard-library/lock-guard-class.md) 和 [unique_lock](../standard-library/unique-lock-class.md) 的构造函数，以指示同样传递给该构造函数的互斥体对象已锁定的对象。  
  
```cpp  
const adopt_lock_t adopt_lock;
```  
  
##  <a name="call_once"></a>  call_once  
 提供在执行期间只调用一次指定的可调用对象的机制。  
  
```
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```  
  
### <a name="parameters"></a>参数  
 `Flag`  
 确保只能调用一次可调用对象的 [once_flag](../standard-library/once-flag-structure.md) 对象。  
  
 `F`  
 一个可调用的对象。  
  
 `A`  
 自变量列表。  
  
### <a name="remarks"></a>备注  
 如果 `Flag` 无效，则函数将引发一个错误代码为 `invalid_argument` 的 [system_error](../standard-library/system-error-class.md)。 否则，模板函数将使用其 `Flag` 参数，以确保它仅成功调用一次 `F(A...)`，而不考虑调用模板函数的次数。 如果通过引发异常退出 `F(A...)`，则该调用未成功。  
  
##  <a name="defer_lock"></a>  defer_lock 变量  
 表示可传递给 [unique_lock](../standard-library/unique-lock-class.md) 的构造函数的对象。 这表示该构造函数不应锁定还将传递给它的 mutex 对象。  
  
```cpp  
const defer_lock_t defer_lock;
```  
  
##  <a name="lock"></a>lock  
 尝试在不死锁的情况下锁定所有自变量。  
  
```cpp  
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```  
  
### <a name="remarks"></a>备注  
 模板函数的参数必须为 mutex 类型，只不过对 `try_lock` 的调用可能会引发异常。  
  
 调用 `lock`、`try_lock` 和 `unlock` 时，该函数会锁定其所有参数，而不会出现死锁。 如果对 `lock` 或 `try_lock` 的调用引发异常，则该函数将在重新引发异常之前，对已成功锁定的任何 mutex 对象调用 `unlock`。  
  
##  <a name="try_to_lock"></a>  try_to_lock 变量  
 表示可以传递给 [unique_lock](../standard-library/unique-lock-class.md) 的构造函数的对象，以指示该构造函数应尝试在不阻止的情况下解锁同样传递给它的 `mutex`。  
  
```cpp  
const try_to_lock_t try_to_lock;
```  
  
## <a name="see-also"></a>另请参阅  
 [\<mutex>](../standard-library/mutex.md)




