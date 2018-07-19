---
title: '&lt;mutex&gt; 函数和变量 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- mutex/std::adopt_lock
- mutex/std::call_once
- mutex/std::defer_lock
- mutex/std::lock
- mutex/std::try_to_lock
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
helpviewer_keywords:
- std::adopt_lock [C++]
- std::call_once [C++]
- std::defer_lock [C++]
- std::lock [C++]
- std::try_to_lock [C++]
ms.openlocfilehash: df52b5bdf9b7054fd838b1892c4e641cdf9d4dcc
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962183"
---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;mutex&gt; 函数和变量

||||
|-|-|-|
|[adopt_lock](#adopt_lock)|[call_once](#call_once)|[defer_lock](#defer_lock)|
|[lock](#lock)|[try_to_lock](#try_to_lock)|

## <a name="adopt_lock"></a>adopt_lock 变量

表示可传递给 [lock_guard](../standard-library/lock-guard-class.md) 和 [unique_lock](../standard-library/unique-lock-class.md) 的构造函数，以指示同样传递给该构造函数的互斥体对象已锁定的对象。

```cpp
const adopt_lock_t adopt_lock;
```

## <a name="call_once"></a>  call_once

提供在执行期间只调用一次指定的可调用对象的机制。

```cpp
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```

### <a name="parameters"></a>参数

*标志*A [once_flag](../standard-library/once-flag-structure.md)对象，以确保可调用对象只能调用一次。

*F*可调用对象。

*一个*参数列表。

### <a name="remarks"></a>备注

如果*标志*不是有效的该函数将引发[system_error](../standard-library/system-error-class.md)的一个错误代码`invalid_argument`。 否则，模板函数将使用其*标志*参数，以确保它调用`F(A...)`成功一次，而不考虑多少次模板函数调用。 如果通过引发异常退出 `F(A...)`，则该调用未成功。

## <a name="defer_lock"></a>  defer_lock 变量

表示可传递给 [unique_lock](../standard-library/unique-lock-class.md) 的构造函数的对象。 这表示该构造函数不应锁定还将传递给它的 mutex 对象。

```cpp
const defer_lock_t defer_lock;
```

## <a name="lock"></a>lock

尝试在不死锁的情况下锁定所有自变量。

```cpp
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```

### <a name="remarks"></a>备注

模板函数的参数必须为 mutex 类型，只不过对 `try_lock` 的调用可能会引发异常。

调用 `lock`、`try_lock` 和 `unlock` 时，该函数会锁定其所有参数，而不会出现死锁。 如果对 `lock` 或 `try_lock` 的调用引发异常，则该函数将在重新引发异常之前，对已成功锁定的任何 mutex 对象调用 `unlock`。

## <a name="try_to_lock"></a>  try_to_lock 变量

表示可以传递给 [unique_lock](../standard-library/unique-lock-class.md) 的构造函数的对象，以指示该构造函数应尝试在不阻止的情况下解锁同样传递给它的 `mutex`。

```cpp
const try_to_lock_t try_to_lock;
```

## <a name="see-also"></a>请参阅

[\<mutex>](../standard-library/mutex.md)<br/>
