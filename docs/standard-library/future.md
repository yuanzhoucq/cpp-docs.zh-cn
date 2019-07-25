---
title: '&lt;future&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: d33b67ed17a95b6717878aaca2f61682b1807c15
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454005"
---
# <a name="ltfuturegt"></a>&lt;future&gt;

包含标准标头 \<future>，以定义模板类和支持模板，它们可简化（可能在单独线程中的）函数运行并检索其结果。 结果可以是由函数返回的值或由函数发出但函数中未捕获的异常。

此标头使用并发运行时 (ConcRT)，以便可将其与其他 ConcRT 机制一起使用。 有关 ConcRT 的详细信息，请参阅[并发运行时](../parallel/concrt/concurrency-runtime.md)。

## <a name="syntax"></a>语法

```cpp
#include <future>
```

## <a name="remarks"></a>备注

> [!NOTE]
> 在使用 **/clr**编译的代码中, 此标头被阻止。

异步提供程序存储函数调用的结果。 异步返回对象用于检索函数调用的结果。 关联异步状态提供一个异步提供程序和一个或多个异步返回对象之间的通信。

程序不会直接创建任何关联异步状态对象。 程序在需要异步提供程序时会创建一个异步提供程序，且随之会创建一个与提供程序共享其关联异步状态的异步返回对象。 异步提供程序和异步返回对象管理保留其共享关联异步状态的对象。 最后一个引用关联异步状态的对象释放状态时，则保留关联异步状态的对象会被销毁。

不具有关联异步状态的异步提供程序或异步返回对象即为空。

只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会为准备就绪。

模板函数 `async` 以及模板类 `promise` 和 `packaged_task` 是异步提供程序。 模板类 `future` 和 `shared_future` 描述异步返回对象。

每个模板`promise`类、 `future`和`shared_future`都具有类型**void**的专用化和按引用存储和检索值的部分专用化。 这些专用化与主模板的唯一区别是用于存储和检索返回值的函数的签名和语义。

模板类`future`和`shared_future`决不会在其析构函数中阻止, 只是为了向后兼容而保留的一种情况:与所有其他先期情况不同 ( `future`对于, 或最后`shared_future` `std::async`一个), 如果任务尚未完成, 则析构函数将阻塞; 即, 如果此线程尚未调用`.get()`或`.wait()`任务仍在运行。 以下可用性说明已添加到草案标准版`std::async`中的说明: "[备注:如果将来从 std:: async 获得的内容移到了本地范围外, 则使用将来的其他代码必须注意未来的析构函数可能会阻塞共享状态。在所有其他情况下, `future` `shared_future`析构函数是必需的, 并且保证永远不会阻止。

## <a name="members"></a>成员

### <a name="classes"></a>类

|name|描述|
|----------|-----------------|
|[future 类](../standard-library/future-class.md)|描述异步返回对象。|
|[future_error 类](../standard-library/future-error-class.md)|描述可由管理 `future` 对象的类型方法引发的异常对象。|
|[packaged_task 类](../standard-library/packaged-task-class.md)|描述作为调用包装器且其调用签名为 `Ty(ArgTypes...)` 的异步提供程序。 除可能的结果外，其关联异步状态还保留可调用对象的副本。|
|[promise 类](../standard-library/promise-class.md)|描述异步提供程序。|
|[shared_future 类](../standard-library/shared-future-class.md)|描述异步返回对象。 相较于 `future` 对象，异步提供程序可与任意数量的 `shared_future` 对象关联。|

### <a name="structures"></a>结构

|名称|描述|
|----------|-----------------|
|[is_error_code_enum 结构](../standard-library/is-error-code-enum-structure.md)|指示 `future_errc` 适合存储 `error_code` 的专用化。|
|[uses_allocator 结构](../standard-library/uses-allocator-structure.md)|始终保持 true 的专用化。|

### <a name="functions"></a>函数

|名称|描述|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|表示一个异步提供程序。|
|[future_category](../standard-library/future-functions.md#future_category)|返回一个描述与 `future` 对象相关联错误的 `error_category` 对象的引用。|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|创建具有 `error_category` 对象（此对象描述 `future` 错误的特点）的 `error_code`。|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|创建具有 `error_category` 对象（此对象描述 `future` 错误的特点）的 `error_condition`。|
|[swap](../standard-library/future-functions.md#swap)|将一个 `promise` 对象的关联异步状态与另一对象的关联异步状态交换。|

### <a name="enumerations"></a>枚举

|名称|描述|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|为 `future_error` 类报告的错误提供符号名称。|
|[future_status](../standard-library/future-enums.md#future_status)|为计时等待函数可返回的原因提供符号名称。|
|[开始](../standard-library/future-enums.md#launch)|表示描述模板函数 `async` 的可能模式的位掩码类型。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
