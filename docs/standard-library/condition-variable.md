---
title: '&lt;condition_variable&gt; | Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <condition_variable>
dev_langs:
- C++
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a54045dfdebf3ab7c9f7ad04611bc9e267faea0d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="ltconditionvariablegt"></a>&lt;condition_variable&gt;

定义类 [condition_variable](../standard-library/condition-variable-class.md) 和 [condition_variable_any](../standard-library/condition-variable-any-class.md)，它们用于创建等待条件变为 true 的对象。

此标头使用并发运行时 (ConcRT)，以便可将其与其他 ConcRT 机制一起使用。 有关 ConcRT 的详细信息，请参阅[并发运行时](../parallel/concrt/concurrency-runtime.md)。

## <a name="syntax"></a>语法

```cpp
#include <condition_variable>
```

> [!NOTE]
> 通过使用编译的代码中 **/clr**，阻止此标头。

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

这些方法各自拥有两个重载版本。 其中一个版本只需等待并可虚假唤醒。 而另一个版本使用其他模板参数定义谓词。 此方法只有在谓词为 `true` 时才会返回。

每个类还具有两种方法，用于通知其条件为 `true` 的条件变量。

- `notify_one` 唤醒等待条件变量的其中一个线程。

- `notify_all` 唤醒等待条件变量的所有线程。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[condition_variable 类](../standard-library/condition-variable-class.md)<br/>
[condition_variable_any 类](../standard-library/condition-variable-any-class.md)<br/>
