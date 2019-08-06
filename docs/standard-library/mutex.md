---
title: '&lt;mutex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <mutex>
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
ms.openlocfilehash: 515318cda2155db81406a5c23cb64e46e79c4e19
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448412"
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

包括：用于定义类 `mutex`、`recursive_mutex`、`timed_mutex` 和 `recursive_timed_mutex` 的标准标头 \<mutex>，模板 `lock_guard` 和 `unique_lock`，以及用于定义互斥代码区域的支持类型和函数。

> [!WARNING]
> 从 Visual Studio 2015 开始, C++标准库同步类型基于 Windows 同步基元, 且不再使用 ConcRT (当目标平台为 Windows XP 时除外)。 \<mutex> 中定义的类型不应与任何 ConcRT 类型或函数共同使用。

## <a name="requirements"></a>要求

**标头:** \<mutex >

**命名空间：** std

## <a name="remarks"></a>备注

> [!NOTE]
> 在使用 **/clr**编译的代码中, 此标头被阻止。

类 `mutex` 和 `recursive_mutex` 是互斥体类型。 互斥体类型的默认构造函数和析构函数不会引发异常。 当多个线程尝试锁定同一对象时，这些对象有方法实现互相排斥。 具体而言，互斥体类型包含的方法有 `lock`、`try_lock` 和 `unlock`：

- `lock` 方法是阻止调用线程，直到线程获取互斥体的所有权。 忽略其返回值。

- `try_lock` 方法尝试在不阻止的情况下获取互斥体的所有权。 如果该方法获取所有权, 则其返回类型可转换为**bool** , 为**true** , 否则为**false**。

- `unlock` 方法是从调用线程中释放互斥体的所有权。

可以使用互斥体类型作为类型参数来对模板 `lock_guard` 和 `unique_lock` 进行实例化。 可以将这些类型的对象作为 `Lock` 自变量以用于模板 [condition_variable_any](../standard-library/condition-variable-any-class.md) 中的等待成员函数。

定时互斥体类型满足互斥体类型的需求。 此外, 它还具有`try_lock_for`和`try_lock_until`方法, 这些方法必须可使用一个参数进行调用, 并且必须返回可转换为**布尔**值的类型。 定时互斥体类型可使用其他自变量来定义这些函数，前提是这些其他自变量都具有默认值。

- `try_lock_for` 方法必须可使用一个自变量 `Rel_time` 进行调用，该自变量的类型是 [chrono::duration](../standard-library/duration-class.md) 的实例化。 此方法尝试获取互斥体的所有权，但无论成功与否，都会在 `Rel_time` 指定的时间内返回。 如果该方法获取所有权, 则返回值将转换为**true** ;否则, 返回值将转换为**false**。

- `try_lock_until` 方法必须可使用一个自变量 `Abs_time` 进行调用，该自变量的类型是 [chrono::time_point](../standard-library/time-point-class.md) 的实例化。 此方法尝试获取互斥体的所有权，但无论成功与否，都会在不迟于 `Abs_time` 指定的时间内返回。 如果该方法获取所有权, 则返回值将转换为**true** ;否则, 返回值将转换为**false**。

互斥体类型也称为可锁定类型。 如果未提供成员函数 `try_lock`，则为基本可锁定类型。 定时互斥体类型也称为定时可锁定类型。

## <a name="members"></a>成员

### <a name="classes"></a>类

|||
|-|-|
|[lock_guard 类](../standard-library/lock-guard-class.md)|表示可进行实例化以创建其析构函数解锁 `mutex` 的对象的模板。|
|[mutex 类（C++ 标准库）](../standard-library/mutex-class-stl.md)|表示互斥体类型。 使用此类型的对象以在程序内强制实现互相排斥。|
|[recursive_mutex 类](../standard-library/recursive-mutex-class.md)|表示互斥体类型。 与 `mutex` 类相反，为已锁定的对象调用锁定方法的行为是有明确定义的。|
|[recursive_timed_mutex 类](../standard-library/recursive-timed-mutex-class.md)|表示定时互斥体类型。 使用此类型的对象以在程序内强制实现有时间限制的互相排斥。 与 `timed_mutex` 类型的对象不同，为 `recursive_timed_mutex` 对象调用锁定方法的效果是有明确定义的。|
|[scoped_lock 类](../standard-library/scoped-lock-class.md)||
|[timed_mutex 类](../standard-library/timed-mutex-class.md)|表示定时互斥体类型。 使用此类型的对象以在程序内强制实现有时间限制的互相排斥。|
|[unique_lock 类](../standard-library/unique-lock-class.md)|表示可进行实例化以创建管理 `mutex` 锁定和解锁的对象的模板。|

### <a name="functions"></a>函数

|||
|-|-|
|[call_once](../standard-library/mutex-functions.md#call_once)|提供在执行期间只调用一次指定的可调用对象的机制。|
|[lock](../standard-library/mutex-functions.md#lock)|尝试在不死锁的情况下锁定所有自变量。|
|[swap](../standard-library/mutex-functions.md#swap)||
|[try_lock](../standard-library/mutex-functions.md#try_lock)||

### <a name="structs"></a>结构

|||
|-|-|
|[adopt_lock_t 结构](../standard-library/adopt-lock-t-structure.md)|表示用于定义 `adopt_lock` 的类型。|
|[defer_lock_t 结构](../standard-library/defer-lock-t-structure.md)|表示定义用于选择 `unique_lock` 的重载构造函数之一的 `defer_lock` 对象的类型。|
|[once_flag 结构](../standard-library/once-flag-structure.md)|表示一个**结构**, 该结构与模板函数`call_once`结合使用, 以确保初始化代码只调用一次, 即使存在多个执行线程。|
|[try_to_lock_t 结构](../standard-library/try-to-lock-t-structure.md)|表示一个**结构**, 该结构`try_to_lock`定义对象并用于选择`unique_lock`的重载构造函数之一。|

### <a name="variables"></a>变量

|||
|-|-|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|表示可传递给 `lock_guard` 和 `unique_lock` 的构造函数，以指示同样传递给该构造函数的互斥体对象已锁定的对象。|
|[defer_lock](../standard-library/mutex-functions.md#defer_lock)|表示可以传递给 `unique_lock` 的构造函数的对象，以指示该构造函数不应锁定同样传递给它的互斥体对象。|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|表示可以传递给 `unique_lock` 的构造函数的对象，以指示该构造函数应尝试在不阻止的情况下解锁同样传递给它的 `mutex`。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
