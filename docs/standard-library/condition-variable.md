---
title: '&lt;condition_variable&gt;'
ms.date: 11/04/2016
f1_keywords:
- <condition_variable>
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
ms.openlocfilehash: d13b58fc05055ceecb6472003d7682c41c76e23d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222532"
---
# <a name="ltcondition_variablegt"></a>&lt;condition_variable&gt;

定义类 [condition_variable](../standard-library/condition-variable-class.md) 和 [condition_variable_any](../standard-library/condition-variable-any-class.md)，它们用于创建等待条件变为 true 的对象。

此标头使用并发运行时 (ConcRT)，以便可将其与其他 ConcRT 机制一起使用。 有关 ConcRT 的详细信息，请参阅[并发运行时](../parallel/concrt/concurrency-runtime.md)。

## <a name="requirements"></a>要求

**标头：**\<condition_variable>

**命名空间:** std

> [!NOTE]
> 在使用 **/clr**编译的代码中，此标头被阻止。

### <a name="remarks"></a>备注

等待条件变量的代码必须也使用 `mutex`。 调用线程必须在其调用等待条件变量的函数前锁定 `mutex`。 然后，`mutex` 将在所调用的函数返回时被锁定。 `mutex` 在线程等待条件变为 true 时不被锁定。 因此，没有不可预知的结果，等待条件变量的每个线程必须使用同一 `mutex` 对象。

`condition_variable_any` 类型的对象可与任何类型的 mutex 一起使用。 所使用的 mutex 类型不一定提供 `try_lock` 方法。 `condition_variable` 类型的对象只能与 `unique_lock<mutex>` 类型的 mutex 一起使用。 此类型的对象可能比 `condition_variable_any<unique_lock<mutex>>` 类型的对象快。

若要等待某个事件，首先锁定 mutex，然后调用条件变量上的其中一个 `wait` 方法。 `wait` 调用在其他线程向条件变量发出信号前将保持阻止状态。

当等待条件变量的线程在没有适当的通知的情况下变为取消阻止时发生*虚假唤醒*。 若要识别此类虚假唤醒，等待条件变为 true 的代码应在代码从等待函数返回时显式检查该条件。 这通常是通过使用循环来实现的；可以使用 `wait(unique_lock<mutex>& lock, Predicate pred)` 为你执行此循环。

```cpp
while (condition is false)
    wait for condition variable;
```

`condition_variable_any` 和 `condition_variable` 类各自拥有等待条件的三种方法。

- `wait` 等待不受限制的时间段。

- `wait_until` 在指定 `time` 前等待。

- `wait_for` 等待指定的 `time interval`。

这些方法各自拥有两个重载版本。 其中一个版本只需等待并可虚假唤醒。 而另一个版本使用其他模板参数定义谓词。 此方法不会返回，直到该谓词为为止 **`true`** 。

每个类还具有两个方法，这些方法用于通知条件变量其条件是 **`true`** 。

- `notify_one` 唤醒等待条件变量的其中一个线程。

- `notify_all` 唤醒等待条件变量的所有线程。

## <a name="functions-and-enums"></a>函数和枚举

```cpp
void notify_all_at_thread_exit(condition_variable& cond, unique_lock<mutex> lk);

enum class cv_status { no_timeout, timeout };
```

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[condition_variable 类](../standard-library/condition-variable-class.md)\
[condition_variable_any 类](../standard-library/condition-variable-any-class.md)
