---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 7053402dfb566f10c7be4c0eebaef40f3d371f43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460075"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

包含标准标头\<线程 > 来定义类**线程**和各种支持函数。

## <a name="syntax"></a>语法

```cpp
#include <thread>
```

## <a name="remarks"></a>备注

> [!NOTE]
> 在使用 **/clr**编译的代码中, 此标头被阻止。

此`__STDCPP_THREADS__`宏定义为一个非零值, 指示此标头支持线程。

## <a name="members"></a>成员

### <a name="public-classes"></a>公共类

|名称|描述|
|----------|-----------------|
|[thread 类](../standard-library/thread-class.md)|定义一个对象, 该对象用于观察和管理应用程序中的执行线程。|

### <a name="public-structures"></a>公共结构

|名称|描述|
|----------|-----------------|
|[hash 结构（C++ 标准库）](../standard-library/hash-structure-stl.md)|定义一个成员函数, 该函数返回由`thread::id`唯一确定的值。 成员函数定义的[哈希](../standard-library/hash-class.md)函数适用于将类型`thread::id`的值映射到索引值的分布。|

### <a name="public-functions"></a>公共函数

|名称|描述|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|唯一标识当前的执行线程。|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|阻止调用线程。|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|阻止调用线程，至少直到指定的时间。|
|[swap](../standard-library/thread-functions.md#swap)|交换两个**线程**对象的状态。|
|[yield](../standard-library/thread-functions.md#yield)|表示要运行其他线程的操作系统，即使当前线程会照常继续运行。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[运算符 > = 运算符](../standard-library/thread-operators.md#op_gt_eq)|确定一个 `thread::id` 对象是否大于或等于另一个。|
|[运算符 > 运算符](../standard-library/thread-operators.md#op_gt)|确定一个 `thread::id` 对象是否大于另一个。|
|[运算符 < = 运算符](../standard-library/thread-operators.md#op_lt_eq)|确定一个 `thread::id` 对象是否小于或等于另一个。|
|[运算符 < 运算符](../standard-library/thread-operators.md#op_lt)|确定一个 `thread::id` 对象是否小于另一个。|
|[operator! = 运算符](../standard-library/thread-operators.md#op_neq)|比较两个 `thread::id` 对象是否相等。|
|[operator = = 运算符](../standard-library/thread-operators.md#op_eq_eq)|比较两个 `thread::id` 对象是否相等。|
|[运算符 < < 运算符](../standard-library/thread-operators.md#op_lt_lt)|将 `thread::id` 对象的文本表示形式插入流。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
