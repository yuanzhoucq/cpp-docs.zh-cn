---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 251a423829a048e3d67b0bcf83107f52c3fdafca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232841"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

包含标准标头 \<thread> 以定义类 `thread` 和各种支持函数。

## <a name="syntax"></a>语法

```cpp
#include <thread>
```

## <a name="remarks"></a>备注

> [!NOTE]
> 在使用 **/clr**编译的代码中，此标头被阻止。

`__STDCPP_THREADS__`此宏定义为一个非零值，指示此标头支持线程。

## <a name="members"></a>成员

### <a name="public-classes"></a>公共类

|名称|说明|
|----------|-----------------|
|[thread 类](../standard-library/thread-class.md)|定义一个对象，该对象用于观察和管理应用程序中的执行线程。|

### <a name="public-structures"></a>公共结构

|名称|说明|
|----------|-----------------|
|[hash 结构（C++ 标准库）](../standard-library/hash-structure-stl.md)|定义一个成员函数，该函数返回由唯一确定的值 `thread::id` 。 成员函数定义的[哈希](../standard-library/hash-class.md)函数适用于将类型的值映射 `thread::id` 到索引值的分布。|

### <a name="public-functions"></a>公共函数

|名称|说明|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|唯一标识当前的执行线程。|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|阻止调用线程。|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|阻止调用线程，至少直到指定的时间。|
|[swap](../standard-library/thread-functions.md#swap)|交换两个对象的状态 `thread` 。|
|[yield](../standard-library/thread-functions.md#yield)|表示要运行其他线程的操作系统，即使当前线程会照常继续运行。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[运算符>= 运算符](../standard-library/thread-operators.md#op_gt_eq)|确定一个 `thread::id` 对象是否大于或等于另一个。|
|[运算符> 运算符](../standard-library/thread-operators.md#op_gt)|确定一个 `thread::id` 对象是否大于另一个。|
|[运算符<= 运算符](../standard-library/thread-operators.md#op_lt_eq)|确定一个 `thread::id` 对象是否小于或等于另一个。|
|[运算符< 运算符](../standard-library/thread-operators.md#op_lt)|确定一个 `thread::id` 对象是否小于另一个。|
|[operator！ = 运算符](../standard-library/thread-operators.md#op_neq)|比较两个 `thread::id` 对象是否相等。|
|[operator = = 运算符](../standard-library/thread-operators.md#op_eq_eq)|比较两个 `thread::id` 对象是否相等。|
|[运算符<< 运算符](../standard-library/thread-operators.md#op_lt_lt)|将 `thread::id` 对象的文本表示形式插入流。|

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
