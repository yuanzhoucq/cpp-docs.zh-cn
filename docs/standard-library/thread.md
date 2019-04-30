---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 43fb79ceda6de7409e6f93797ce2f4ff213c43ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411976"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

包括标准标头\<线程 > 来定义此类**线程**和各种支持的函数。

## <a name="syntax"></a>语法

```cpp
#include <thread>
```

## <a name="remarks"></a>备注

> [!NOTE]
> 在使用已编译的代码 **/clr**，禁止使用此标头。

`__STDCPP_THREADS__`宏被定义为非零值指示此标头支持线程。

## <a name="members"></a>成员

### <a name="public-classes"></a>公共类

|名称|描述|
|----------|-----------------|
|[thread 类](../standard-library/thread-class.md)|定义用于查看和管理的应用程序中的执行线程的对象。|

### <a name="public-structures"></a>公共结构

|名称|描述|
|----------|-----------------|
|[hash 结构（C++ 标准库）](../standard-library/hash-structure-stl.md)|定义了成员函数返回一个值，通过唯一确定`thread::id`。 此成员函数定义[哈希](../standard-library/hash-class.md)适用于类型的映射值的函数`thread::id`到索引值的分布。|

### <a name="public-functions"></a>公共函数

|名称|描述|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|唯一标识当前的执行线程。|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|阻止调用线程。|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|阻止调用线程，至少直到指定的时间。|
|[swap](../standard-library/thread-functions.md#swap)|交换两个状态**线程**对象。|
|[yield](../standard-library/thread-functions.md#yield)|表示要运行其他线程的操作系统，即使当前线程会照常继续运行。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator>= Operator](../standard-library/thread-operators.md#op_gt_eq)|确定一个 `thread::id` 对象是否大于或等于另一个。|
|[运算符 > 运算符](../standard-library/thread-operators.md#op_gt)|确定一个 `thread::id` 对象是否大于另一个。|
|[运算符 < = 运算符](../standard-library/thread-operators.md#op_lt_eq)|确定一个 `thread::id` 对象是否小于或等于另一个。|
|[运算符 < 运算符](../standard-library/thread-operators.md#op_lt)|确定一个 `thread::id` 对象是否小于另一个。|
|[operator!= Operator](../standard-library/thread-operators.md#op_neq)|比较两个 `thread::id` 对象是否相等。|
|[运算符 = = 运算符](../standard-library/thread-operators.md#op_eq_eq)|比较两个 `thread::id` 对象是否相等。|
|[operator<< Operator](../standard-library/thread-operators.md#op_lt_lt)|将 `thread::id` 对象的文本表示形式插入流。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
